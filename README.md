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

- [`views/_tumblr_vars.jade`](/views/_tumblr_vars.jade) - Declare tumblr-controllable variables
  - Useful for colors and text that the client would like to edit themselves

- [`views/index.jade`](/views/index.jade) The compiled output of this folder will serve as your Tumblr source.

- [`views/<index|permalink>_content.jade`](/views/index/_content.jade) - Contains all content types per specific Tumblr state (Index or Permalink)

- [`views/tumblr_types/<type>`](/views/tumblr_types) - Holds markup for a specific type (i.e. Photo)
  - Generally, you'll want to include an `_index.jade` and a `_permalink.jade` for each content type. These will map to their corresponding `IndexPage` and `PermalinkPage` respectively.
  - Add/remove tumblr content types as is needed. Reference the Tumblr docs for more information on any given content types and their associated variables.

  Example: Adding a `panorama` content type to [Permalink](/views/permalink) content
  ```jade
  //- Panorama Posts

  | {block:Panorama}

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
