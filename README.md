# Formatting and Publishing a Resume Using Markdown and a Static Site Generator
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
The following steps describe how to create, format, and publish a resume using Markdown and a static site generator. Each step follows standard instruction-writing principles, including using clear action verbs and separating individual actions into distinct steps.
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
### 3. Write the resume in Markdown
_Etter recommends using lightweight markup languages because they separate content from presentation and are easy to maintain._
1. Create a new Markdown file for the resume.
2. Use headings to structure major sections.
3. Use bullet points to list responsibilities and achievements.
4. Use links to reference external profiles.
5. Save the file in your static site generator.
### 4. Configure the Static Site Generator 
_Etter's principles recommend separating writing from formatting. Static site generators transforms Markdown files into HTML._
1. Install a static site generator that supports Markdown (e.g [Pelican](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://getpelican.com/&ved=2ahUKEwjy8fnU8v-SAxX91fACHS3uGm8QFnoECAwQAQ&usg=AOvVaw3eG5fI2lv2gpNTPquE20j5)).
2. Create a new site using the generator's setup command.
