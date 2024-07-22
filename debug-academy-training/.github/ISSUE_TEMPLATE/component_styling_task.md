---
name: Component Styling Task Template
about: How to start a task & submit work, etc
title: 'Create & Style COMPONENT_NAME Component'
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

## The Component
This section describes the component. More specific instructions follow afterwards.

### Component Name and expected variables
- Component Name: Teaser with Thumbnail (`COMPONENT_NAME`)
- Expected Variables
  - Thumbnail (This will later be populated with an HTML image tag (such as `demo_image_html`))
  - Title
  - Summary
  - Link (This variable's value will later be populated with an HTML anchor tag (such as `demo_link_text_html`))

### How it looks
We're styling the following component:
[PLACE IMAGE OF COMPONENT HERE]

## Specific implementation instructions

Run the following command to create your twig and SASS file(s):
`ddev newcomponent COMPONENT_NAME`
Replace COMPONENT_NAME with the name of your component.

What the "ddev newcomponent" script is doing:

### What happens when we run "ddev newcomponent COMPONENT_NAME"
The "`ddev newcomponent COMPONENT_NAME`" script does all of the following for us (Note: "COMPONENT_NAME" should be replaced with the component's name):
*   It creates a folder named `COMPONENT_NAME/` within our custom theme's templates/components/ directory.
    *   In that folder, the command creates 2 files:
        *   `_COMPONENT_NAME.html.twig`
        *   `_COMPONENT_NAME.scss`
*   Ensures your new .scss file gets compiled to CSS in the future by adding an import statement to our custom theme's scss/import.scss file
    *   Adds the following line to the custom theme's existing scss/import.scss file: `@import "../templates/components/COMPONENT_NAME/_COMPONENT_NAME";`

## Edit the files
*   Begin writing appropriate HTML and Twig logic for the component within \_COMPONENT_NAME.html.twig
    *   You will need to populate the twig file yourself. Use twig variables when a value in the design should be dynamic/pulled from the content. You can name them whatever you like. Variables should correspond to the Fields from the "Name and fields" section within this issue.

### Write CSS/SASS for our component

*   Edit our new component's .scss file
*   Then look at the design and write appropriate CSS/SASS to make the styling match.
*   The workflow for writing / testing SASS is:
    *   Write some CSS (or SASS) styling in VSCode
    *   SSH into your development environment's command line
        *   **Git Bash users**: `winpty ddev ssh`
        *   Everyone else: `ddev ssh`
    *   Within your development environment, cd into your custom theme:
        *   `cd web/themes/custom/port_theme`
    *   Compile your theme's SASS as usual
        *   `sass scss/style.scss css/style.css`

### Edit the "demo.html.twig" file for your component

To see your component's HTML and CSS in your website:

*   Open your preferred code-friendly text editor (such as VSCode)
*   Open your theme's components folder:
    *   drupal/web/themes/custom/port\_theme/templates/components
*   In your component's folder `components/COMPONENT_NAME`, edit the file named: `demo.html.twig`
    *   Open the demo.html.twig file in your preferred code-friendly text editor


Update the include statement to customize it for *your* component:
Within this include statement, be sure to populate all of your component's variables with placeholder values. You do this by adding a with {} statement with variables on the left and values on the right. The file is automatically populated with an example. You can find possible values for the variables in the section above, labeled *Component Name and expected variables* It should look something like this:
  ```
  {% include '@port_theme/components/COMPONENT_NAME/_COMPONENT_NAME.html.twig' with {
  one_variable: "Some value",
  another_variable: demo_link_image_html
  } %}
  ```
 
### Preview your work

*   Ensure you've compiled the most recent version of your SASS
    *   SSH into your environment
    *   cd into your custom theme
    *   Compile your SASS
*   The "ddev newcomponent" command already edited demo\_page.html.twig for us. The file is located at:
    *   port\_theme/templates/components/demo\_page.html.twig
    *  This file's contents are displayed on the /demo path of our website.
*   Clear your drupal site's cache
    *   `drush cr`
*   Visit the page /demo on your website
*   You should be able to see what your component looks like so far, likely towards the bottom of the page.

### Finish styling your component

Continue adjusting the Twig and SCSS of your component until you are satisfied with its styling.

Once satisfied, commit the component's Twig and SASS files.

That's it for now! We'll handle the "Theming" / "integration" step in a separate task.

# Committing & Submitting
Prefix all git commits with the Github Issue Number as shown here:
git commit -m '#123 - Commit Message.' Replace 123 with the issue number (which can be found in the URL)

Great job!  Now would be a great time to [export your configurations and commit your work](https://debugacademy.com/task/drpl3mo-8).  We'll style the content type's display view mode in an upcoming task.
