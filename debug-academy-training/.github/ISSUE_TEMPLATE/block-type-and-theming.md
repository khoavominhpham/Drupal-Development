---
name: Block type & Theming
about: 'Create block type and apply styling to it ("A.K.A. theme it")'
title: 'Create a custom Block Type for the "BLOCK_TYPE" Component'
labels: 'Site Building, Theming (Twig + Drupal FE)'
assignees: ''

---

# New task preparation
SEE: "UPDATE_ME" placeholders

Leave a comment on this issue when  you decide to work on it, then leave another comment when you have an update (submitted work or a question).

It is OK for multiple people to work on the same tasks in parallel!

## Classwork task preparation
Complete the steps listed in the "[Prepare to work on today's Classwork](https://debugacademy.com/assignment/3307)" task. This will automatically commit any work in progress to a new branch and automatically prepare your local development environment for the next task.

## Non-classwork task preparation
First, complete all steps listed in "[How to start a new task](https://debugacademy.com/task/drpl3mo-59)" . This will reset your local development website to a clean starting point.

# Overview
## What we're building
We already have styling (with dummy content) for the following:
UPDATE_ME
<img width="1134" alt="Screenshot 2023-11-20 at 7 50 12 AM" src="https://github.com/debugacademy/port22/assets/1713958/c4b3eee1-89e0-4a36-99ec-a10d48edbb6f">

Visit /demo on your website to take a look at the styling.

It looks good with the dummy content - but we also want content editors to be able to reuse that styling for content they create!

Because the style is intended to be a reusable component which may be placed within multiple pages, we can create a "Block Type" for it. This will give editors a way to input their own values. We'll name the block type BLOCK_TYPE.

As we can see in the image above, content editors should be able to populate the following fields on the block type:
UPDATE_ME
- Banner image
- Title
- Body

## Part 1: Create the block type
1.  Log in to your Drupal website as administrator
2.  Visit Structure > Block layout > Block types
3.  Press "Add a custom block type" to create a new block type
4.  Enter BLOCK_TYPE as the block type's name
5. Continue to the next step.

### Add appropriate fields to the block type
Visit the block type's "Manage fields" page/tab to add or remove fields.

All **block types come with an optional "title" field and a "body" fields** by default.

You won't see the title field on any block type's "Manage fields" page, but it will appear when users create blocks.

Block types' body field can be deleted via the "Manage fields" page when it's not needed.

Press \+ Add field to add any other fields needed by the component. Reference the "What we're building" section above to see what fields are needed.

Be sure to select appropriate field types and to review each field's settings!

Save your block type.

### Test the new block type

1.  After adding your fields, test your new block type
    *   Create a new Basic Page (Content > Add Content > Basic Page)
    *   Click the "Layout" tab to use the Layout Builder
        *   _If you do not see it_, you can first [enable the layout builder module for the Basic Page content type](/assignment/2801)
    *   Press \+ Add Block
    *   Press + Create custom block
    *   Select the Banner block type
    *   Populate the block's fields
    *   Create the block by pressing "Add block"
    *   Press "Save layout" to save the block's placement on the page (you may need to scroll up to find this button)
    *   Confirm you were able to create a block with the required fields

At this point, we've created a block type and confirmed that we can use it to populate the fields and create multiple blocks.

However, the block type is not yet using the styling from the component. Let's apply the component's styling to this block next.

### Commit the block type
Now would be a great time to [export your configurations and commit your work](https://debugacademy.com/task/drpl3mo-8).

Prefix all git commits with the Github Issue Number as shown here:
git commit -m '#123 - Commit Message.' Replace 123 with the issue number (which can be found in the URL)

Continue below to Part 2 (on the same branch) to apply the styling to your new block type!

## Part 2: Theme the block type
Because the styled component is also completed and merged, you can proceed to apply the styling to the block type you just created!

This means we'll make our block types look like the components which we previously wrote Twig + SASS for.

### Override the block's default HTML (twig)
To apply our component's styling to our block, we need to replace our block's HTML with our component's HTML.

#### Determine the appropriate filename
On the landing page you just created, right click one of the blocks you placed.

Press "Inspect Element" to view the page source (HTML).

Scroll up very slowly, reviewing each line along the way. Look for the section of code that says `<!-- THEME HOOK: 'block' -->`. It will resemble the following:
```
<!-- THEME DEBUG -->
<!-- THEME HOOK: 'block' -->
<!-- FILE NAME SUGGESTIONS:
   * block--inline-block--my-block.html.twig
   * block--inline-block.html.twig
   * block--content-above.html.twig
   * block--olivero-page-title.html.twig
   * block--core.html.twig
   x block.html.twig
-->
<!-- BEGIN OUTPUT from 'core/themes/olivero/templates/block/block.html.twig' -->
```

Directly underneath `<!-- THEME HOOK: 'block' -->`, you should see a list labeled "`FILE NAME SUGGESTIONS:`". These are the filenames you can use to overwrite your block's HTML.

Which should you use? Ensure you select a filename that:
- Begins with the word "block" (because we want to overwrite our block's HTML)
- Mentions your BLOCK_TYPE by name (i.e. "block.html.twig" is too generic - it would apply to ALL block types.)
- Accurately describes only what you're trying to apply the styling to

new filename will likely <em>start with</em>:&nbsp;block--inline-block--

For example, the appropriate filename will likely <em>start with</em>: `block--inline-block--`

Determined your filename? Great! Time to create the file..
#### Create your block's Twig file
Open your website in VSCode via the command line:
- `cd ~/Sites/debugacademy/drupal`
- `code .`

In VSCode's sidebar, navigate to your theme's templates/ folder:
- web/themes/custom/THEME_NAME/templates/

Right click on the "templates" folder and press "New file" to create a new file.

Name the new file using the filename determined in the previous step (e.g. "block--*something*.html.twig")

In your newly created Twig file, start with the following code:
```
<div{{ attributes }}>
  {{ title_prefix }}
  {{ title_suffix }}
  My block will be placed here!
</div>
```

Save & commit the new Twig file.

Clear your site's cache and refresh your page. If you successfully overwrote the block's HTML (Twig), you should see the words "My block will be placed here!" where your block used to be.

#### Copy the styling into our block

Let's take the completed styling and apply it to our block type, usng the block's field values to populate the styled component.

In VSCode, open our styled component's demo.html.twig file. The demo.html.twig file will be located at:
- web/themes/custom/*THEME_NAME*/templates/components/*COMPONENT_NAME*/demo.html.twig

Now COPY the full "include" statement from demo.html.twig. This will begin with `{% include` and end with `%}`.

Replace the words "My block will be placed here!" in your block's twig file by pasting the include statement you just copied.

Clear your site's cache and refresh your page. If you performed the last step successfully, you should now see the styling with the dummy values in your block.

#### Replace the dummy values with appropriate field values
Replace the sample variable values with appropriate field values from the block type.

The block's title can be found in the `label` variable. How do we know this? By reviewing the comments at the top of the *original* (now overridden) Twig file -- the comments contain useful information.
More information on determining field values follows this section:

<em>For example</em>, your code updates may be <em>similar</em> to this:

<strong>Before:</strong>
```
  with {
    title: "Welcome"
```
<strong>After:</strong>
```
  with {
    title: "label"
```

##### Determinig the field values' variables
To access the rest of the block's fields, do the following:
- Ensure the fields are not in the Disabled sections of the display mode:
<ul>
  <li>​​​​​​Structure &gt; Block layout &gt; Block types</li>
  <li>Click Manage Display next to the block type you're working on</li>
  <li>Ensure you're editing the correct display tab (typically "default" for blocks)</li>
  <li>Ensure no relevant fields are listed under the "Disabled" section. If they are, move them above the disabled section.</li>
  <li>Configure each field's display appropriately (e.g. Hide the field's "label" if not needed. Adjust other display settings for the field if appropriate.)</li>
  <li>Don't forget to "Save" these changes</li>
</ul>
- Determine the field's machine name through the UI:
<ul>
  <li>​​​​​​Structure &gt; Block layout &gt; Block types</li>
  <li>Click Manage fields next to the block type you're working on</li>
  <li>See the fields' machine names listed in the "Machine name" column</li>
</ul>
- In your block's Twig file, replace the dummy values with field variables.
<ul>
  <li>To determine field variables, combine the fields' machine names with the "content" variable.</li>
  <li>For example, for the machine names "body" and "field_image", the variables would be "content.body" and "content.field_image".</li>
  <li>After replacing all dummy values in your block twig file, save the file</li>
</ul>

Clear your site's cache and refresh your page. You should now see real values in your styled component!

Struggling to find the appropriate value for a field? Try to research, then reach out to an instructor for help!

#### Refine field output as needed
By default, most of the field values you just populated should <em>work</em>, but they might not be formatted according to your needs.

##### Removing HTML from field output
Drupal typically outputs fields with a wrapping &lt;div&gt; tag. Do any of your fields&nbsp;<strong>need</strong> that HTML wrapper (e.g. &lt;div&gt;) removed? For example, a plain URL being passed into a component as an href's attribute?
<ul>
  <li>If a field needs the wrapping div removed from its output, try appending `.0` to the end of it. For example:
  <ul>
    <li>Before: <code>content.field_plain_url</code>
    <ul>
      <li>This displays the content from field_plain_url surrounded by a wrapper, such as <code>&lt;div class="field"&gt;https://google.com&lt;/div&gt;</code></li>
    </ul>
    </li>
    <li>After: <code>content.field_plain_url.0</code>
    <ul>
      <li>This displays the content from field_plain_url without&nbsp;a&nbsp;wrapper, such as <code>https://google.com</code></li>
    </ul>
    </li>
  </ul>
  </li>
</ul>

##### Changing output settings
For example, let's say you're passing an image into your styled component by using `content.field_image`.

What if it's displaying an image which is linked to itself, but you want it to output the image without it being linked to anything. You can adjust the image field's output from fields on the block type's "Manage Display" page.

Additional examples: You want to hide a field's label, you want to trim a field's output to a certain number of characters, you want to display the URL to an image instead of the image itself.. etc.

Here's how:
<ul>
  <li>Visit the block type's manage display page to configure how field values are displayed.
  <ul>
    <li>For example, you can choose whether each field's label should display or not. Here's how:
    <ul>
      <li>​​​​​​Structure &gt; Block layout &gt; Block types</li>
      <li>Click <strong>Manage Display</strong> next to the block type you're working on</li>
      <li>Change the settings for each field, as needed</li>
    </ul>
    </li>
  </ul>
  </li>
</ul>

##### Adjust the styled component itself
Hopefully this step isn't necessary -- but just in case:

Struggling to format Drupal's fields the way the styled component is expecting? The good news is that we have full control of the styled component.

Instead of fighting with our field's output, we can edit the styled component so that it is more compatible with the markup (HTML) Drupal's fields naturally provide us with.

If this applies, feel free to edit the component's files (Twig & SASS) as needed.

### Render the rest of {{ content }}
The `{{ content }}` variable includes more than just the fields. For example, it may include caching information.

To ensure we don't lose that information, be sure to render (print) the rest of the `{{ content }}` variable. This can be done using the twig `|without()` filter (to avoid printing fields twice).

For example, if you already printed the fields `body` and `field_image`, you could then print the content variable using: `{{ content|without('body', 'field_image') }}` . This can be added anywhere in your block's twig file.

## Final testing!
Clear your site's cache and refresh your page. Your component should now have the appropriate styling AND content! You've just empowered our content editors to apply the component's style to their content. Nice.

# Committing & Submitting
Prefix all git commits with the Github Issue Number as shown here:
git commit -m '#123 - Commit Message.' Replace 123 with the issue number (which can be found in the URL)

Great job!  Now would be a great time to [export your configurations and commit your work](https://debugacademy.com/task/drpl3mo-8).  We'll style the content type's display view mode in an upcoming task.
