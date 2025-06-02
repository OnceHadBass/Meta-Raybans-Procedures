# Meta-Raybans-Procedures
A way of having Meta Raybans glasses speak step by step SOPs to you using Tasker and some little tricks

# NFC Procedure Database

An open standard for embedding step-by-step instructions in NFC tags, enabling hands-free guided procedures - Tasker reads the next instruction when you tap the glasses and this audible from the glasses.

## 🎯 Vision

Imagine scanning an NFC tag on any device / recipe book / spare part / landmark etc. and instantly getting voice-guided instructions on how to use it / cook it / install it / navigate around it. This project creates an open standard where anyone can embed procedures in NFC tags and having those instructions be navigable via the Raybans glasses. It's still a little glitchy so please excuse those.

## 🚀 Use Cases

- **Manufacturing equipment** - Safe startup and operation procedures hands free.
- **Recipes** - Recipe instructions as you make it - but at your pace - no pressure!
- **Spare Parts** - Installation instructions hands free as you work.
- **Office devices** - Setup and troubleshooting guides
- **Emergency procedures** - Critical safety instructions - helping you move faster hands free
- **Training materials** - Learn about any part / item / thing just be scanning it - learning at the point of use
- **Accessibility** - Voice-guided assistance for any process

## 📱 How It Works

1. **Create** procedures using the web interface - the interface sanity checks procedures (length and profanity) and then logs them to the project giving that a UID and a json.
2. **Generate** NFC tags by imprinting them with the procedure UID and json URL - you can use the NFC tools app for this 
3. **Scan** tags with your phone - YOU NEED TO INSTALL THE TASKER APK FOR THIS PROJECT - to start your voice-guided instructions
4. **Follow** Tap the right side glasses leg and get the next instruction.

## 🏗️ Architecture

### NFC Tag Format
Each NFC tag contains:
```
procedure_id|https://yourdomain.github.io/procedure-database/procedures/procedure_id.json
```

### JSON Procedure Format
```json
{
  "title": "Coffee Machine Setup",
  "instructions": [
    {"step": 1, "instruction": "Fill water reservoir with fresh water"},
    {"step": 2, "instruction": "Insert coffee pod into chamber"},
    {"step": 3, "instruction": "Press brew button"},
    {"step": 4, "instruction": "Wait for completion beep"}
  ]
}
```
COMMENT - I'm considering making this json structure more complex for more options e.g. tools for this step - maybe you double tap the glasses for those or something.

### Local Caching
- Procedures are cached locally after first download
- Works offline after initial sync
UPDATING - right now, there's no way to update a procedure once it's in the database. I need to figure that out but right now this is a proof of concept.

## 🔧 Setup

### 1. Fork This Repository
Click "Fork" to create your own procedure database.

### 2. Enable GitHub Pages
- Go to Settings → Pages
- Source: Deploy from branch `main`
- Your database will be available at: `https://yourusername.github.io/procedure-database/`

### 3. Create Procedures
- Visit your GitHub Pages URL
- Use the web interface to create new procedures
- Each procedure generates a unique JSON file

### 4. Set Up NFC Reader (Android + Tasker)
- Install Tasker app
- Import the provided Tasker profile (coming soon)
- Configure your trusted domain URL
- Start scanning NFC tags!

## 📝 Creating Procedures

### Web Interface
1. Visit your GitHub Pages site
2. Enter procedure title and steps
3. Generate JSON file
4. Create NFC tag with the provided ID and URL

### Manual Creation
Create files in `procedures/` folder:
- Filename: `your_procedure_name.json`
- Format: Follow the JSON structure above
- Limits: Max 50 steps, 200 characters per instruction

## 🛡️ Security & Quality

### Trusted Sources
- Only procedures from verified domains are executed
- Domain validation prevents malicious content
- Local size limits prevent abuse

### Content Guidelines
- Keep instructions clear and concise
- Test procedures before publishing
- Avoid dangerous or inappropriate content
- Use simple language for accessibility

## 🤝 Contributing

### Adding Procedures
1. Fork this repository
2. Create procedure JSON files in `procedures/` folder
3. Submit pull request with your additions
4. Community review and approval

### Improving the Platform
- Bug reports and feature requests welcome
- Code contributions appreciated
- Documentation improvements needed

## 📋 Roadmap

- [ ] **v1.0** - Basic voice-guided procedures
- [ ] **v1.1** - Multi-language support
- [ ] **v1.2** - Visual aids and images
- [ ] **v2.0** - Conditional branching ("If X, then Y")
- [ ] **v2.1** - User progress tracking
- [ ] **v3.0** - IoT device integration

## 🔗 Example Procedures

This repository includes sample procedures:
- `coffee_machine_setup.json` - Basic appliance operation
- `printer_startup.json` - Equipment initialization
- `test_simple.json` - Simple demo procedure

## 📱 Compatible Apps

Currently supported:
- **Android + Tasker** - Full voice guidance
- **Web interface** - Procedure creation and management

## 📄 License

MIT License - See [LICENSE](LICENSE) for details.

This project is designed to be an open standard. Use it, modify it, build on it!

## 🆘 Support

- **Issues**: Report bugs and request features via GitHub Issues
- **Discussions**: Join conversations in GitHub Discussions
- **Documentation**: Check the Wiki for detailed guides

## 🌟 Star This Project

If you find this useful, please star the repository to help others discover it!

---

**Made with ❤️ for the maker community**

*Don't let Meta stop you doing cool stuff with your Meta Raybans :) Turn every object into a voice-guided experience, one NFC tag at a time.*
