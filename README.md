Tumblr on Roots
===============

# What it do?
Tumblroots aims at building tumblr themes with ease. By leveraging the power of the [roots framework](http://roots.cx) and establishing sensible defaults, tumblr theme building just became a bit easier.

### Setup/Installation
- clone project
- `roots watch`

`Developed using roots version 2.1.0 (stable)`

### Tumblroots Structure
- [`views/layout.jade`](/views/layout.jade) - Main website layout
  - Feel free to nest content as you see fit. By default, the index page is wrapped in a container, as is each permalink page
- [`views/_tumblr_vars.jade`](/views/_tumblr_vars.jade) - Declare tumblr-controllable variables
  - Useful for colors and text that the client would like to edit themselves
- [`views/_content.jade`](/views/_content.jade) - Standard tumblr layout (includes all content types)
  - As with the layout, feel free to restructure this layout as you see fit
- [`views/tumblr_types/<type>`](/views/tumblr_types) - Holds markup for a specific type (i.e. Photo)
  - Generally, you'll want to include an `index.jade` and a `show.jade` for each content type. These will map to their corresponding `IndexPage` and `PermalinkPage` respectively.
  - Add/remove tumblr content types as is needed. Reference the Tumblr docs for more information on any given content types and their associated variables.

  Example: Adding a `panorama` content type to [`views/_content.jade`](/views/_content.jade)
  ```jade
  //- Panorama Posts

  | {block:Panorama}
  | {block:IndexPage}

  li.post.text
    include tumblr_types/panorama/index

  | {block:IndexPage}

  | {block:PermalinkPage}

  li.post.text
    include tumblr_types/panorama/show

  | {/block:PermalinkPage}
  | {/block:Text}
  ```

### Recommended Tumblr Deploys
Until a better solution surfaces, it is advisable to follow these steps when deploying a tumblr theme:

- compile project (`roots compile`)
- extract assets (images, stylesheets, js, etc) to an S3 bucket
- copy contents of `public/index.html` with local assets pointing to their S3 equivalents (a global find and replace will suffice)
- manually paste this `.html` theme into the `Customize > Edit HTML` editor

### Tumblr Theme Resources
- Tumblr Custom Theme "API" Docs
[http://www.tumblr.com/docs/en/custom_themes]()
