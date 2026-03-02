# Formatting and Publishing a Resume Using Markdown and Pelican
## Statement of Purpose
This document explains how to format a resume using Markdown and publish it as a static website hosted on a forge. It entails the practical steps required to complete this task, including creating, version-control, generating and deploying the site using modern documentation tools. The instructions are tailored for readers with basic command-line skills, base knowlegde of Markdown and little to no experience with Git or static site generators. In addition to describing the technical workflow, this README connects steps to key principles from Andrew Etter's *Modern Technical Writing*, demonstrating how lightweight markup languages, distributed version control systems, static site generators, and forges support great technical communication.

## Prerequisites 
_Listing prerequisites up front follows Etter's recommendation to reduce reader friction by anticipating what the reader will need before they begin the process._
In order to completely carry out this set of instructions, the reader should have access to the following resources:
* Computer (MacOs, Windows or Linux)
* Terminal (Command Prompt, Terminal)
* Python (to run Pelican)
* Text Editor (nano, VS Code, etc.)
* GitHub account (hosting the repository & live site)
* Git installed (version control & publishing to GitHub)
    * Run these quick commands to confirm all necessary tools are installed:
      ```bash
      python3 --version
      pip3 --version
      git --version

## Instructions
The following steps describe how to create, format, and publish a resume using Markdown and a static site generator. Each step follows standard instruction-writing principles, including using clear action verbs and containing only one action per step.
### 1. Create a Project Directory 
_Etter recommends storing documentation close to its source files using version control._ Begin by creating a new project directory. 
1. Open a terminal
2. Create a new directory for the project:
   ```bash
   mkdir resume-site
3. Navigate into the directory
   ```bash
   cd resume-site
### 2. Initialize Version Control
_Etter emphasizes the importance of distributed version control systems for managing documentation. Version control allows changes to be tracked, reviewed and shared._ 
1. Initiallize a Git repository in the project directory:
   ```bash
   git init
2. Create a remote repository on your chosen forge.
3. Connect the local repository to the remote repository:
   ```bash
   git remote add origin <repository-url>
### 3. Install Pelican
_Using a static site generator supports Etter’s principle of separating content from presentation. Pelican generates a website from Markdown files without requiring you to write raw HTML._
1. Install Pelican with Markdown support:
   ```bash
   python3 -m pip install "pelican[markdown]"
2. Verify pelican is installed:
   ```bash
   pelican --version
### 4. Create a Pelican Site
_Etter's principles recommends standardizing documentation workflows. A setup tool reduces repeated manual work, helping achieving standardization._
1. Run Pelican's quickstart command:
   ```bash
   pelican-quickstart
2. Create the site in the current directory by entering:
   ```bash
   Welcome to pelican-quickstart v4.11.0.post0.
   This script will help you create a new Pelican-based website.
   
   Please answer the following questions so this script can generate the files needed by Pelican:
   
   Where do you want to create your new web site? [.] .
   What will be the title of this web site? _Your Site Name_
   Who will be the author of this web site? Marvin McLaren
   What will be the default language of this web site? [en] en
   Do you want to specify a URL prefix? e.g., https://example.com (Y/n) n
   Do you want to enable article pagination? (Y/n) n
   What is your time zone? [Europe/Rome] America/Winnipeg
   Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n) y
   Do you want to upload your website using FTP? (y/N) n
   Do you want to upload your website using SSH? (y/N) n
   Do you want to upload your website using Dropbox? (y/N) n
   Do you want to upload your website using S3? (y/N) n
   Do you want to upload your website using Rackspace Cloud Files? (y/N) n
   Do you want to upload your website using GitHub Pages? (y/N) n
   Done. Your new project is available at /home/user/yourusername.chosenforge.io
   
   $ ls
   content		Makefile	output		pelicanconf.py	publishconf.py	tasks.py
3. Generate Pelican Site locally
   ```bash
   make html
   make serve
4. Preview Pelican Site locally
   Navigate the link output from `make serve` to preview site:
   ```bash
   Serving site at: http://127.0.0.1:8000 - Tap CTRL-C to stop
### 5. Add the Resume as a Page
Pelican organizes content inside the `content/` directory. Placing the resume inside this folder allows Pelican to generate it as a page in the final website.
1. Navigate to the content directory:
   ```bash
   cd content
2. Create a `pages` directory
   ```bash
   mkdir pages
3. Navigate into the pages directory
   ```bash
   cd pages
4. Create file named `resume.md`
   ```bash
   touch resume.md
5. Add metadata at the top of the file:
   ```markdown
   Title: Resume
   Date: 2026-03-01
   Slug: resume
6. Using Markdwon syntax, write the content of the resume below the metadata
7. Save the file:
   ```bash
   Ctrl + X
   Return
### 6. Add a Home Page
Adding a resume ensures that the resume is accessible from the main URL of the site.
1. Return to the content directory:
   ```bash
   cd ..
2. Create a file named `index.html`
   ```bash
   touch index.html
3. Add metadata at the top of the file:
   ```markdown
   Title: Home
   Date: 2026-03-01
   Slug: index
4. Add a short introductory paragraph to the home screen.
5. Add a link to the resume page:
   ```markdown
   [Tap here to view Resume](/pages/resume.html)
6. Save the file
   ```bash
   Ctrl + X
   Return
