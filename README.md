# Formatting and Publishing a Resume Using Markdown and Pelican
## Statement of Purpose
This document explains how to format a resume using Markdown and publish it as a static website hosted on a forge. It describes the practical steps required to create, version-control, generate, and deploy the site using modern documentation tools. The instructions are written for readers with basic command-line skills and introductory knowledge of Markdown, but little to no experience with Git or static site generators. In addition to outlining the technical workflow, this README connects each step to key principles from Andrew Etter’s *Modern Technical Writing*, demonstrating how lightweight markup languages, distributed version control systems, static site generators, and forges support effective technical communication.

## Prerequisites 
_Listing prerequisites in advance follows Etter’s recommendation to anticipate reader needs and reduce unnecessary friction._ Before beginning, ensure you have access to the following:
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
      ```
## Instructions
The following steps describe how to create, format, and publish a resume using Markdown and Pelican. Each step begins with a clear action verb and contains only one action, in accordance with standard instructional writing principles:
### 1. Create a Project Directory 
_Etter recommends managing documentation within version-controlled project structures._
1. Open a terminal
2. Create a new directory for the project:
   ```bash
   mkdir resume-site
   ```
3. Navigate into the directory
   ```bash
   cd resume-site
   ```
### 2. Initialize Version Control
_Distributed version control allows documentation to be tracked, revised, and shared. Etter emphasizes that documentation should be treated like code._ 
1. Initiallize a Git repository in the project directory:
   ```bash
   git init
   ```
### 3. Install Pelican
_Using a static site generator supports Etter’s principle of separating content from presentation. Pelican generates a website from Markdown files without requiring you to write raw HTML._
1. Install Pelican with Markdown support:
   ```bash
   python3 -m pip install "pelican[markdown]"
   ```
2. Verify pelican is installed:
   ```bash
   pelican --version
   ```
### 4. Create a Pelican Site
_Etter's principles recommends standardizing documentation workflows. A setup tool reduces repeated manual work, achieving standardization._
1. Run Pelican's quickstart command:
   ```bash
   pelican-quickstart
   ```
2. When asked where to create the website, enter::
   ```text
   .
   ```
3. When asked for the default language, enter:
   ```text
   en
   ```
4. When asked whether to specify a URL prefix, enter:
   ```text
   n
   ```
5. When asked whether to generate a Makefile/tasks file, enter:
   ```text
   y
   ```
6. For upload options (FTP/SSH/Dropbox/S3/GitHub Pages), enter:
   ```text
   n
   ```
### 5. Add the Resume as a Page
_Etter recommends lightweight markup languages such as Markdown because they are readable in plain text and easy to maintain over time. Writing the resume in Markdown keeps the content adaptable and version-controlled._
1. Navigate to the content directory:
   ```bash
   cd content
   ```
2. Create a `pages` directory
   ```bash
   mkdir pages
   ```
3. Navigate into the pages directory
   ```bash
   cd pages
   ```
4. Create file named `resume.md`
   ```bash
   touch resume.md
   ```
5. Add metadata at the top of the file:
   ```markdown
   Title: Resume
   Date: 2026-03-01
   Slug: resume
   ```
6. Using **Markdwon syntax**, write the content of the resume below the metadata
7. Save the file:
   ```bash
   Ctrl + X
   Return
   ```
### 6. Add a Home Page
Adding a resume ensures that the resume is accessible from the main URL of the site.
1. Return to the content directory:
   ```bash
   cd ..
   ```
2. Create a file named `index.html`
   ```bash
   touch index.html
   ```
3. Add metadata at the top of the file:
   ```markdown
   Title: Home
   Date: 2026-03-01
   Slug: index
   ```
4. Add a short introductory paragraph to the home screen.
5. Add a link to the resume page:
   ```markdown
   [Tap here to view Resume](/pages/resume.html)
   ```
6. Save the file
   ```bash
   Ctrl + X
   Return
   ```
### 7. Preview the website
_Generating the site converts Markdown files into static HTML output._ To preview the website:
1. Return to project root directory:
   ```bash
   cd ..
   ls
   content		Makefile	output		pelicanconf.py	publishconf.py	tasks.py
   ```
2. Generate Pelican Site locally
   ```bash
   make html
   ```
3. Start the local server:
    ```bash
   make serve
   ```
3. Preview Pelican Site locally 
   ```bash
   Serving site at: http://127.0.0.1:8000 - Tap CTRL-C to stop
   ```
   Navigate the link output from `make serve` to preview site. 
### 8. Publish to GitHub Pages 
_Hosting documentation on a forge ensures public accessibility and version control. Etter argues that modern documentation should be distributed and easily shareable.._
1. Open GitHub in a web browser.
2. Click **New Repository**
3. Name your repository:
   ```text
   <your-username.github.io>
   ```
4. Set repository to public
5. Click **Create Repository**
6. Add the remote repository
   ```bash
   git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
   ```
7. Add the project files:
   ```bash
   git add .
   ```
8. Commit the files:
   ```bash
   git commit -m "Initial Pelican source files"
   ```
9. Push to the main branch
    ```bash
    git push -u origin main
    ```
10. Build site:
    ```bash
    make html
    ```
11. Copy the generated files to the repository root:
    ```bash
    cp -R output/* .
    ```
12. Create a file named .nojekyll:
    ```bash
    touch .nojekyll
    ```
13. Commit the published files:
    ```bash
    git add .
    git commit -m "Publish site"
    ```
14. Push Changes:
    ```bash
    git push
    ```
### 9. Verify Development
1. Visit
   ```text
   https://<your-username>.github.io
   ```
2. Confirm that the home page loads
3. Confirm that the resume link works too

## Further Resources
The following resources provide additional background information on the tools and concepts used in this project:
* [Pelican Documentation](https://docs.getpelican.com/)
* [GitHub Pages Documentation](https://docs.github.com/en/pages)
* [Python Official Documentation](https://docs.python.org/3/)
* [The Markdown Guide](https://www.markdownguide.org/)

## FAQ
### 1. Why is Markdown better than writing raw HTML?
Markdown is quicker to write and easier to read than raw HTML. It lets you focus on organizing content (headings, lists, links) without dealing with HTML tags. It is also easier to update over time, and static site generators can convert it into HTML automatically.
### 2.  I changed my resume in Markdown. Why don’t I see the changes when I refresh the website?
This is because the website is static. Updating the Markdown file does not automatically update the generated HTML.
* To see changes locally: run `make html`, then run `make serve`, then refresh your browser.
* To update the live site: rebuild the site `make html`, then commit and push the updated generated files to the branch that GitHub Pages publishes.

## Credits
