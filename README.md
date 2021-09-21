# Lab 5: Project management with Git, GitHub, and RStudio Cloud

<!-- NOTE: 
You can preview this README.md document by clicking the 'Preview' button in the RStudio toolbar. 
-->

## Preparation

- Read/ annotate: [Recipe \#5](https://lin380.github.io/tadr/articles/recipe_5.html). You can refer back to this document to help you at any point during this lab activity.
- Note: do your best to employ what you've learned and use other existing resources (R documentation, web searches, etc.).

## Objectives

- Set up a GitHub account. 
- Fork and copy a GitHub repository to RStudio Cloud.
- Use R, Git, and GitHub to manage, store, and publish changes to a project.

## Instructions

### Setup

1. Create a new R Markdown document. Title it "Lab #5" and provide add your name as the author. 
2. Edit the front matter to have rendered R Markdown documents print pretty tabular datasets.
3. Delete all the material below the front matter.
4. Add a code chunk directly below the header named 'setup' and add the code to load the following packages and any others you end up using in this lab report.
  - tidyverse

### Tasks

1. Create two level-1 header sections named: "Project setup" and "Description".
2. Follow the instructions that follow adding the relevant prose description and code chunks to the corresponding sections.

#### Project setup

Follow the steps below. After completing these steps, provide a prose description of what you have done. 

**GitHub account and forked repository**

- Create a [GitHub account](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home). Use your Wake email. 
- (Optional) Modify your GitHub profile `README.md`. 
- Navigate to the [lin380/project_template repository](https://github.com/lin380/project_template) and fork this repository (this will create a copy in your own GitHub repository listing)
- In the Settings for this forked repository, change the name of the repository to `project_<your_lastname>`. 


**RStudio Cloud project based on forked repository**

- Navigate to [RStudio Cloud LIN 380 Workspace](https://rstudio.cloud/spaces/162391/projects). 
- Create a New Project and select 'New Project from Git Repository'. In this space paste the URL from your forked version of the project template.
- Once the project has load in RStudio Cloud, load the usethis and gitcreds library in the R Console.
- Then, run the `use_git_config()` function with the arguments `user.name` and `user.email` set to your GitHub username and email address. 
  - To check that your correct GitHub username and email credentials are set in Git move to the Terminal and run `git config --global --list`
- Now run the `create_github_token()` function (no arguments). This will open your GitHub account. The only option to change is to set the token to expire in 90 days. 
- Copy the personal access token (PAT) and save it somewhere save on your computer. You will need access to it and this will be the only time you will be able to see it on GitHub. 
- Return to your RStudio Cloud project and run `gitcreds_set()` and paste your PAT when prompted. 
  - Note: this process will need to be repeated every 12 hours, for security.

You are now ready to make changes to your project! Before we make any project-specific changes, let's run the `_pipeline.R` script. This will have the effect of generating a website for this project.

You can run this script one of two ways: 

1. In the R Console run `source("_pipeline.R")`. 
2. Open the `_pipeline.R` file and in the toolbar click 'Source'

In either case, the script will be run. This has the effect of knitting all of the `.Rmd` files in the `analysis/` directory and generating a functioning website that resides in the `docs/` directory. 



**Update GitHub**

Now that we have effectively changed the project, let's run through the workflow to interact with Git to add, commit, and push the changes to GitHub.

In the Terminal ...

- Run `git status` to see the modified and untracked files and directories
- Run `git add -A` to add all modifications and untracked files to the staging area
- Run `git status` again to view what has been staged
- Run `git commit -m "First commit"` to make a snapshot of the staged files and directories as they currently are. 
- Run `git push` to send the committed files and directories to GitHub (note: this will fail if the PAT has expired. If it has, you will need to run `gitcreds_set()` again in the R Console and paste your PAT before running this command again.)

Navigate to your GitHub profile. You should now see the updates and the name of the latest commit (in this case "First commit") where file and directories were just updated. 

**Enable GitHub Pages**

We want our website to show up so we need to make a couple adjustments on GitHub. In the GitHub repository for your project, go to the Settings tab. Then on the left skim down to the 'Pages' tab. Select 'main' as the branch and `/docs` as the folder. Click 'Save. You will get a notification of the URL where your website can now be found. Copy this URL. Navigate back to the main repository view. Beside the 'About' heading on right, click on the cog icon. You can change the description and paste the URL in the field for the 'Website'. Save the changes.

You are good to go! You now have a working website on GitHub Pages!

**Start working!**

You can now start editing your project to make it yours. Here are some suggestions: 

- Edit the `README.md`: 
  - delete the `# Notes on formatting Markdown documents` info
  - change the title of the project??
- Edit the `analysis/_site.yml`: 
  - change the `title:` attribute's value
  - change the URL to *your* GitHub repository.
    - For example, mine is `https://github.com/jerid-francom/project_francom`
  - change the `theme:` attribute value to another theme such as: 
    - `default`, `cerulean`, `journal`, `flatly`, `darkly`, `readable`, `spacelab`, `united`, `cosmo`, `lumen`, `paper`, `sandstone`, `simplex`, and `yeti` (from the [Bootstrap library](https://bootswatch.com))

Source the `_pipeline.R` file to see the changes. If you are happy, you can add, commit, and push the changes to GitHub to see them take effect on your website!


#### Description

1. Provide the URL to your GitHub Pages site for your project.
2. In your own words, describe the practical workflow for subsequent updates/additions to your project.
3. Assess the structural elements of this project template. What do you find and how to they align with the guiding principles for 'Communicable' research given in Chapter 4 "Framing research" in the Text as Data course book?

### Assessment

Add a level-1 section which describes your learning in this lab.

Some questions to consider: 

  - What did you learn?
  - What was most/ least challenging?
  - What resources did you consult? 
  - What more would you like to know about?

## Submission

1. To prepare your lab report for submission on Canvas you will need to Knit your R Markdown document to PDF or Word. 
2. Download this file to your computer.
3. Go to the Canvas submission page for Lab #5 and submit your PDF/Word document as a 'File Upload'. Add any comments you would like to pass on to me about the lab in the 'Comments...' box in Canvas.
