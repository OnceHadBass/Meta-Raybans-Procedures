BLISST
A tool for creating and deploying hands-free lists and procedures to your Meta Ray-Ban Smart Glasses.

BLISST uses Tasker and some hacky workarounds to bypass the locked-down OS on Meta Raybans glasses, enabling navigation of shareable, geo=locatable lists using the built-in media controls (tap on the glasses arm).

🎯 Vision
Imagine scanning a QR code or NFC tag on any device, recipe book, spare part, or landmark and instantly getting voice-guided instructions on how to use it, cook it, install it, or learn about it. This project makes that possible today, providing a simple web tool to create and deploy procedures that can be navigated hands-free via your glasses. It's a tech demo; pardon our querks.

📱 How It Works
Create procedures using the BLISST web interface (Github Pages). The app sanity-checks your list and prepares it for deployment.
Generate a unique JSON file and hosting URL by clicking "Upload & Get Link". The app then provides triggers for this procedure.
Imprint the NFC string to a tag, share the QR code or url to the list, or download it direct to your mobile device.
When you scan the generated QR code or NFC tag, or download the procedure direct, this starts the procedure. 
The procedure is run using Tasker profiles on your Android device. If you're wearing your Raybans you'll hear the list through your glasses.
Follow the instructions spoken through your glasses. Tap the glasses' touch-sensitive arm (the media control) to advance to the next step.

Note - Tasker and Spotify both need to be open to run lists.

🚀 Use Cases
Shopping List - Create yourself a shopping list. Walk round the supermarket without needed to get your smartphone / paper list out.
Recipes - Share a recipe. Let people folow it at their own pace without needing to keep pulling out a phone.
Exercise Routines - Be guided through your workout, one step at a time.
Industrial & Office - Tag machines with NFC tags which process hands-free startup and maintenance procedures.
Emergency Procedures - Scan QR codes and follow critical safety instructions quickly and without using your hands.
Point-of-Use Training - Learn about any item, part, or exhibit just by scanning it.
Accessibility - Provide voice-guided assistance for any process.

🏗️ Architecture
Trigger Formats
BLISST uses three types of triggers to launch a procedure:

QR Code: Contains a standard HTTPS link to a landing page (landing.html) which ensures maximum compatibility with all scanners. Click the button on the landing page to download the procedure and run it. https://your-github-username.github.io/your-repo-name/landing.html?uid=procedure_id&file=file_url

NFC Tag: Contains a pipe-separated string with the procedure's unique ID and its direct JSON file URL. Imprint this to any NFC tag and then scan it to download and run the procedure.
procedure_id|https://hosted-file-url.com/procedure_id.json

Direct Download: If you create a list from the browser on your phone you can download it directly and run it. Good for shopping lists etc.

JSON Procedure Format
Each procedure is stored as a simple JSON object with a title and an array of instructions.

JSON

{
  "title": "Coffee Machine Setup",
  "uid": "a1b2c3d4",
  "instructions": [
    { "step": 1, "instruction": "Fill water reservoir with fresh water" },
    { "step": 2, "instruction": "Insert coffee pod into chamber" },
    { "step": 3, "instruction": "Press brew button" }
  ]
}

Backend Service
File hosting is handled by a simple proxy server running on Glitch. This allows the web app to upload and host the generated JSON files without needing a complex backend.

🔧 Setup
For Users
Install Tasker: You must have the Tasker app installed on your Android phone.

Import Project: Download the BLISST_Tasker_Project.xml.txt file from this repository: [LINK TO YOUR TASKER XML FILE HERE].

In Tasker, long-press the "Home" icon (🏠) and select "Import Project", then choose the file you downloaded.
Enable the project by making sure the toggle next to its name is on. You're ready to start scanning!
For Developers (Self-Hosting)

If you want to host your own instance of BLISST:

Fork This Repository: Click "Fork" to create your own copy.
Enable GitHub Pages: In your forked repo, go to Settings → Pages. For the source, select "Deploy from a branch" and choose the main branch.
Update URLs in index.html:
In the displayFinalLinks function, change the baseUrl variable to your own GitHub Pages URL.
(Optional) If you set up your own hosting backend, change the proxyUrl variable in the handleUpload function.

📝 Creating Procedures
The easiest way to create procedures is via the web interface hosted on your GitHub Pages site.

Visit your GitHub Pages URL.
Enter a procedure title and add your steps.
Click Generate Procedure to review the data.
Click Upload & Get Link to publish the list and get your QR/NFC triggers.

🛡️ Security & Quality
Content Filtering: The web app includes a basic profanity filter to prevent inappropriate language in procedure titles and steps.
Hosting: The backend service is simple and does not execute any code, it only hosts static .json files.
Content Guidelines: Please keep instructions clear, concise, and safe. Test your procedures before creating public triggers for them.

🤝 Contributing
This is a proof-of-concept project, and improvements are welcome.

Bug reports and feature requests can be submitted via GitHub Issues.
Code contributions via Pull Requests are appreciated.
Documentation improvements are always needed.

📄 License
This project is distributed under the MIT License. See the LICENSE file for details.

🆘 Support
Issues: Report bugs and request features via GitHub Issues.
Discussions: Join conversations in GitHub Discussions.

🌟 Star This Project
If you find this project useful or interesting, please star the repository to help others discover it!

Made with ❤️ for the maker and smart glasses community.

Turn any object into a voice-guided experience, one QR code or NFC tag at a time.
