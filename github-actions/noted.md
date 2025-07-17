# Introduction to GitHub Actions
GitHub Actions is a CI/CD pipeline directly integrated with your GitHub repository.

GitHub Actions allows you to automate:

Running test suites
Building images
Compiling static sites
Deploying code to servers
and more…
GitHub Actions has templates you can use to get started.

GitHub Actions files are defined as YAML files located in the .github/workflow folder in your repo.

You can have multiple workflows in the repo triggered by different events.

Within a GitHub repo, you’ll have a tab for Actions.

```sh
on
  push:
    branches: | $default-branch |
  workflow_dispatch:
env:
  AZURE_WEBAPP_NAME: your-app-name
  AZURE_WEBAPP_PACKAGE_PATH: '.'
  NODE_VERSION: '14.x'
permissions:
  contents: read
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    ...
```


# GitHub Actions Basics Follow Along

# Objective

This guide will walk you through the basics of GitHub Actions, including forking a repository, exploring the UI, understanding workflows, and executing a basic action.

# Prerequisites
A GitHub account
Basic understanding of repositories and GitHub navigation




# Step 1: Forking the Repository
1.1
Open the repository provided in the course materials.
✋
1.2
Click on the Fork button (top-right corner) to create a copy of the repository in your GitHub account.
✋
1.3
Once the fork is complete, navigate to your forked repository.
✋
Step 2: Exploring GitHub Actions UI
Accessing the Actions Tab
2.1
Click on the Actions tab in your repository.
✋
2.2
Observe any existing workflows that may have been previously run.
✋
2.3
If there are no workflows, don’t worry—we will create one shortly.
✋
Exploring the Settings Tab
2.4
Click on the Settings tab.
✋
2.5
Navigate to Actions on the left sidebar.
✋
2.6
Review the options under Action Permissions, including:
✋
Allow all actions and reusable workflows
Disable Actions
Allow selected actions and reusable workflows
2.7
Look at Artifact and log retention settings, set to 90 days by default.
✋
2.8
Review Fork pull request workflows from outside collaborators settings.
✋
Step 3: Understanding Workflows and YAML Files
Locating Workflows in the Repository
3.1
Navigate to the Code tab.
✋
3.2
Open the .github/workflows/ directory.
✋
3.3
Notice that workflow files are stored in .yml or .yaml format.
✋
Analyzing an Example Workflow
3.4
Open an existing workflow .yml file.
✋
3.5
Identify key components:
✋
name: Defines the workflow name.
on: Specifies events that trigger the workflow (e.g., push, pull_request).
jobs: Defines a job and its execution environment.
runs-on: Specifies the OS environment (e.g., ubuntu-latest).
steps: Lists the tasks executed in sequence.
uses: Refers to GitHub Actions or third-party actions.
Step 4: Creating a New Workflow
Using a Template
4.1
Go to the Actions tab.
✋
4.2
Click New Workflow.
✋
4.3
Select a template (e.g., "Greet First-Time Contributors").
✋
4.4
Modify the workflow file as needed.
✋
Manually Creating a Workflow
4.1
Navigate to the Code tab.
✋
4.2
Open .github/workflows/.
✋
4.3
Create a new file called greetings.yml.
✋
4.4
Add the following content:
✋
   name: Greet First-Time Contributors
   on:
     issues:
       types: [opened]
   jobs:
     greeting:
       runs-on: ubuntu-latest
       steps:
         - name: Welcome Message
           uses: actions/first-interaction@v1
           with:
             repo-token: ${{ secrets.GITHUB_TOKEN }}
             issue-message: 'Thanks for opening your first issue!'
             pr-message: 'Thanks for your first contribution!'
4.5
Commit the file.
✋
Step 5: Running the Workflow
Triggering the Workflow
5.1
Go to the Issues tab.
✋
5.2
Click New Issue.
✋
5.3
Create a dummy issue to trigger the workflow.
✋
5.4
Go to Actions and observe the workflow running.
✋
Reviewing Workflow Execution
5.6
Click on the running workflow in the Actions tab.
✋
5.7
Observe the steps executed.
✋
5.8
Check the logs for output messages.
✋
Step 6: Disabling or Deleting a Workflow
Disabling a Workflow
6.1
Go to the Actions tab.
✋
6.2
Click on the workflow you want to disable.
✋
6.3
In the top-right corner, click Disable Workflow.
✋
Deleting a Workflow
6.4
Navigate to the Code tab.
✋
6.5
Open .github/workflows/.
✋
6.6
Delete the unwanted workflow file.
✋
6.7
Commit the changes.
✋
6.8
Go back to Actions—the deleted workflow should no longer appear.
✋
Step 7: Cleaning Up
7.1
Go to the Actions tab.
✋
7.2
Delete previous workflow runs (optional).
✋
7.3
If you want to keep your workflows but avoid running them, move .yml files to a different folder (e.g., templates/).
✋
Summary
Forked a repository to enable GitHub Actions.
Explored GitHub Actions UI and settings.
Created, triggered, and analyzed a simple workflow.
Disabled and deleted workflows as needed.
Gained hands-on experience with workflow YAML files.