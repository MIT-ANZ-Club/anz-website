# MIT Australia and New Zealand Club Website
<img src="assets/images/anz-logo.png" alt="MIT" width="250" style="align:center"/>

This repo contains the website for the MIT ANZ Club.
See the live website on http://anz.mit.edu

This site is set up with [Jekyll](https://github.com/jekyll/jekyll) and 
[Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) which uses Ruby.
The decision was made to use these libraries as they allow for easy setup, editing and flexibility.


**Table of Contents**

- [Installation](#installation-instructions)
- [Updating the Website](#updating-the-website)
- [Deployment](#deploying-to-the-live-website)

___

## Installation Instructions
1. Install Jekyll and Ruby: https://jekyllrb.com/docs/installation/
   - Ruby 3.1 is what I use. The website should build fine on Ruby 2.7+ though.
2. Clone the repo
   ```bash
   git clone git@github.com:MIT-ANZ-Club/anz-website.git
   ```
3. Build the website and serve it locally with live reloading using
   ```ruby
   cd anz-website
   bundle exec jekyll serve --livereload -P 8888
   ```
   - Any changes you make should be reflected in the live site.
   - If you don't include `bundle exec` you may get dependency errors, especially on Ruby 2.7.
   - The default port is 4000, but you can use the `-P` flag to change it.

## Updating the Website
Jekyll uses Markdown files to generate the website. You can check out this 
[Jekyll Markdown Cheatsheet](https://itopaloglu83.github.io/Jekyll-Markdown-Cheat-Sheet/).

### Adding a new page
You can add a new page by adding a markdown file in the `_pages` directory.
Check the existing pages for examples.

To add a new page to the navigation bar, edit `_data/navigation.yml` to include the title and URL to your new page

Check the [Minimal Mistakes documentation](https://mmistakes.github.io/minimal-mistakes/docs/pages/) for layout and more details.

### Modifying an existing page
The existing pages are in the `_pages` directory.
You can update the content of the page using Markdown.

### Adding Images
Images for the website are currently in the `assets/images` directory.
You can add new image there and reference them in your markdown files. 

### Editing the contact form
The contact form is powered by [Formspree](https://formspree.io/).
The mailing list form is in `_includes/mailing-list-form.html`.

You should ask William Shen for help to update the contact form, as it is tied to his Formspree account.

## Deploying to the Live Website
**TL;DR: in 1 command:**
```bash
JEKYLL_ENV=production jekyll build && \
  rsync -r _site/ athena.dialup.mit.edu:/mit/anz/web_scripts/ && \
  echo "Deployed to http://anz.mit.edu"
```

You will need to authenticate with your Kerberos account and Duo. Instructions for setting up access to Athena can be found here: https://web.mit.edu/dialup/www/ssh.html


We use the [scripts service](https://scripts.mit.edu/) run by SIPB to host the website.
Basically, we build the static website locally and then upload it to the AFS locker for the 
ANZ club within the scripts service.

**Detailed Instructions**:
1. Build the website using `JEKYLL_ENV=production jekyll build`
    - The `JEKYLL_ENV=production` environment variable tells Jekyll to build the website with production mode 
      (includes Google Analytics in our case).
2. Jekyll will build the website into the `_sites` directory
3. Upload the files in `_sites` to the `/mit/anz/web_scripts/` AFS locker on Athena. You can use rsync or scp for this.
    - Run `rsync -r _site/ athena.dialup.mit.edu:/mit/anz/web_scripts/`
4. Don't forget to commit your changes to Github!

