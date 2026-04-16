## 👋 Hello Contributors!
Thank you for contributing to our project. It's an honour. Please follow the following guidelines to make sure that your Pull Request gets accepted and your project gets added into the system.
**EMPTY TEMPLATES FOR FILES LIKE "PACKAGE.JSON" AND YOUR PART OF "INDEX.JSON" ARE AT THE END OF THIS FILE. PLEASE READ UNTIL THE END**

### 1) Repo File Structure
Your package must adhere to this structure.
Add a new folder below the packages with your package name.
```
repo/
 ├─ index.json
 └─ packages/
    └─ yourpackage/
       ├─ package.json
       └─ main.sk
```

### 2) package.json Structure
Only touch the *package.json* of your own projects! *package.json* must follow this structure to get recognised properly. This is an example.
```
{
  "name": "anticheat",
  "displayname": "Advanced AntiCheat",
  "version": "1.2.0",
  "description": "Advanced anti-cheat skripts with powerful tools for moderation. Lorem ipsum with more text I need this text to be longer so this is just jargon just skip to the next line!",
  "author": "efenow",
  "website": "https://skriptpacks.dev/anticheat",

  "media": {
    "logo": "https://cdn.skriptpacks.dev/logos/anticheat.png",
    "youtube": "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
    "screenshots": [
      "https://cdn.skriptpacks.dev/ss/anticheat1.png",
      "https://cdn.skriptpacks.dev/ss/anticheat2.png"
    ]
  },

  "depends": ["economy"],

  "pluginDepends": {
    "SkBee": ">=2.8.0",
    "Vault": ">=1.7.3"
  },

  "skript": ">=2.7",

  "tags": ["security", "anticheat", "utility"],
  "minServer": "1.20",
  "license": "MIT"
  },

  "security": {
    "status": "verified",
    "risk": 12,
    "lastScan": "2026-01-26"
}
```
  Skript name: "anticheat" ***(MUST MATCH FOLDER NAME!)***
  You'll be able to upload your images to *skriptpacks.dev/upload*. **Any other source will not be allowed.**
  This example skript depends on the example **Skript** *"economy"* (the Skript must be in our repo), the **plugins** *"Skbee"* and *"Vault"* with the specified versions. If these plugins with the given versions aren't installed, the plugin will not be able to install and/or run.
  You can see the *"security"* tab. We'll get to that in a second.

### 3) index.json Structure
***index.json*** is a universal file in the core of the repo which acts like a map for the web and plugin client. It points to your project folder and is a catalog of the main information of all projects. Due to the core importance of this file, you **must only touch your own sections of index.json**. Pull requests are thoroughly checked for the changed sections. If we find a section where you, knowingly or not, touch a section of index.json which you are not allowed to you will recieve a comment in your pull request asking you to fix it.
Here's an example section of *index.json* for the same example Skript
```
{
  "anticheat": {
    "version": "1.2.0",
    "name": "Advanced AntiCheat",
    "short": "Stops cheaters using Skript",
    "logo": "https://cdn.skriptpacks.dev/logos/anticheat.png",
    "tags": ["security", "utility"],
    "url": "/packages/anticheat"
  }
}
```
  Notice the "name" section is not the same as the one in the title, or in the package.json file. It's the same as the *Display Name* section. This is because this is the *Display Name* of your project. So, the title name is just an ID but whatever.
  The ***description** section* of *package.json* is not the same as the ***short** section* of index.json. This is because *description* is the full description of the project while *short* is a brief comment about what the project does.
  **Warning:** There are sections what we call ***"common sections"***. These sections have to be the same between *package.json* and *index.json*. In this example; the title name, *"logo"*, *"version"* and *"tags"* are all common sections. These two must be the same or the project will be broken.

### 4) AI Security and Moderation
**Now before you think this is some AI Jargon, calm down!** This is a pretty logical system which protects servers from installing "virus" Skripts. We need this because we can't hand-inspect every single project that gets sent, we don't have that kind of time and we don't have that kind of money to outsource it.
I'm going to explain this in detail because as a project maintainer, you need to understand this system to pass the security checkpoint.
Diagram of how it works:
```
Project Maintainer Upload (this is you)
      │ you upload the project via pr
      ▼
 Pre-Check (Format, JSON, Lint)
      │ repo maintainers (us) check to make sure formatting is
      ▼ right (this is also where the profanity check happens)
 AI Scan (Groq / LLM)
      │ An LLM we select at GroqCloud scans
      ▼ the Skript for malicious code
 Risk Score (0-100)
      │
 ┌────┴────┐
 ▼         ▼
AUTO PASS  STAFF REVIEW
 (0-49)      (50-100)
  Gets     Goes to hand
uploaded    inspection
```
Example output of what we get from the LLM
```
{
  "risk": 72,
  "flags": [
    "Potential OP escalation",
    "Remote command execution",
    "Hidden webhook call"
  ],
  "summary": "Script attempts to grant operator permissions under certain chat triggers."
}
```
***This project goes to hand inspection***

