---
name: Create Views
about: How to start a task & submit work,
title: 'Create "VIEW_NAME" view of ENTITY_TYPE (BUNDLE_TYPE)'
labels: 'Site Building'
assignees: ''

---

# New task preparation
SEE: "UPDATE_ME" placeholders
## Classwork task preparation
Complete the steps listed in the "[Prepare to work on today's Classwork](https://debugacademy.com/assignment/3307)" task. This will automatically commit any work in progress to a new branch and automatically prepare your local development environment for the next task.

## Non-classwork task preparation
First, complete all steps listed in "[How to start a new task](https://debugacademy.com/task/drpl3mo-59)" . This will reset your local development website to a clean starting point.

# Overview
In Drupal, we create most dynamic lists of entities as "views" - even if the dynamic list only contains 1 item!

The goal of this task is to create the "VIEW_NAME" view with a block display of ENTITY_TYPE (specifically, BUNDLE_TYPE). More information follows..

# The view we're creating
We are creating a view as a block. This view will dynamically list BUNDLE_TYPE.
UPDATE_ME: [INSERT IMAGE HERE]

## Creating the View block
1. Log in as administrator
2. Visit Manage > Structure > Views > Add new view (/admin/structure/views)
3. Name the view "VIEW_NAME"
4. Show ENTITY_TYPE of type BUNDLE_TYPE
5. Create a block
6. Click Save and Edit
7. Under format, next to "Show:", click "Fields". Instead of Fields, select an appropriate entity display UPDATE_ME (e.g. "Content" or "Media"). Next, select an appropriate display mode (e.g. "Teaser" or "Media Library")
8. Configure the pager to display UPDATE_ME items
9. Add a filter using the "UPDATE_ME" field.
11. Save View

## Test the block
### Create ENTITY_TYPE of type BUNDLE_TYPE
1. Create three "BUNDLE_TYPEs".
UPDATE_ME
4. Save them

### Place the view on a page
For testing, place the View Block using the Layout Builder

*   Content > Add Content > Basic Page
    *   For the Page's Title, add "Testing view"
    *   Click Save
*   Place the Block using the Layout Builder
    *   Click the "**Layout**" tab
    *   Click "**Add Block**"
        *   Then, from the pop-out menu, scroll down to the "Lists (Views)" subheading and select our View block ("VIEW_NAME")
        *   Then, click "Add block" -- the default settings are fine for now.
*   Scroll up to the top of the page, and click "**Save Layout**"
*   Great job!  We now created our block and placed it using the Layout Builder.

Now take a look at the basic page you created. Does your view show UPDATE_ME? If yes, great! You've created your view correctly.

# Committing & Submitting
Prefix all git commits with the Github Issue Number as shown here:
git commit -m '#123 - Commit Message.' Replace 123 with the issue number (which can be found in the URL)

Great job!  Now would be a great time to [export your configurations and commit your work](https://debugacademy.com/task/drpl3mo-8).  If applicable, we'll style the view and/or BUNDLE_TYPE in an upcoming task.
