---
name: General Styling Task Template
about: How to start a task & submit work, etc
title: ''
labels: ''
assignees: ''

---

# New task preparation

## Classwork task preparation
Complete the steps listed in the "[Prepare to work on today's Classwork](https://debugacademy.com/assignment/3307)" task. This will automatically commit any work in progress to a new branch and automatically prepare your local development environment for the next task.

## Non-classwork task preparation
First, complete all steps listed in "[How to start a new task](https://debugacademy.com/task/drpl3mo-59)" . This will reset your local development website to a clean starting point.

# Overview
Note: for styling assignments, you can find the design on "Webflow". Because Webflow uses
HTML and CSS, you can use your browser's inspector tool to determine color codes and more. Find the
design here: https://drupal-tv.webflow.io/table-of-contents

## What we're styling
This section describes what will be styled as part of this task. Technical instructions follow afterwards.

### Name and fields
- Name: Teaser with Thumbnail (`teaser_thumbnail`)
- Variables
  - Thumbnail (This will later be populated with an HTML image tag (such as `demo_image_html`))
  - Title
  - Summary
  - Link (This variable's value will later be populated with an HTML anchor tag (such as `demo_link_text_html`))

### How it looks
Find examples in the webflow design: https://drupal-tv.webflow.io/table-of-contents

## Specific implementation instructions

### Write CSS/SASS in the appropriate file(s)

Most site-wide SASS will be written in style.scss, located within our theme's scss folder:

*   In a non-SSH comment line window, open your site's files in VSCode:
    *  `cd ~/Sites/debugacademy/drupal`
*   In VSCode's left sidebar, navigate to the appropriate SASS file:
    *  web/themes/custom/port_theme/scss/style.scss
*   The workflow for writing / testing SASS is:
    *   Write some CSS (or SASS) styling in VSCode
    *   SSH into your development environment's command line
        *   **Git Bash users**: `winpty ddev ssh`
        *   Everyone else: `ddev ssh`
    *   Within your development environment, cd into your custom theme:
        *   `cd web/themes/custom/port_theme`
    *   Compile your theme's SASS as usual
        *   `sass scss/style.scss css/style.css`
    *   Clear the site's cache:
        *   `drush cr`
    *   Refresh your website to view the changes
        *   In a NON-SSH'ed command line, run: `ddev launch`

### Preview your work

*   Ensure you've compiled the most recent version of your SASS
    *   SSH into your environment
    *   cd into your custom theme
    *   Compile your SASS
*   Clear your drupal site's cache
    *   `drush cr`
*   If necessary, create content on the website
*   You should be able to see your CSS changes

### Continue styling

Continue adjusting the SCSS until you are satisfied.

Once satisfied, commit your changes!

# Committing & Submitting
Prefix all git commits with the Github Issue Number as shown here:
git commit -m '#123 - Commit Message.' Replace 123 with the issue number (which can be found in the URL)

Great job!  Now would be a great time to [export your configurations and commit your work](https://debugacademy.com/task/drpl3mo-8).  We'll style the content type's display view mode in an upcoming task.
