# MIT Australia and New Zealand Club Website

This site is set up with [Jekyll](https://github.com/jekyll/jekyll) and 
[Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes).
The decision was made to use these libraries as they allow for easy setup, editing and flexibility.

## Installation Instructions
1. Install Jekyll (and Ruby): https://jekyllrb.com/docs/installation/
2. Clone the repo
3. Build the website and serve it locally with live reloading using `jekyll serve --livereload`

### Adding a new page
You can add a new page by adding a markdown file in the `_pages` directory.
Check the existing pages for examples.

To add a new page to the navigation bar, edit `_data/navigation.yml` to include the title and URL to your new page

Check the [Minimal Mistakes documentation](https://mmistakes.github.io/minimal-mistakes/docs/pages/) for layout and more details.

### Pushing your changes to the Live Website

1. Build the website using `JEKYLL_ENV=production jekyll build`
    - The `JEKYLL_ENV=production` environment variable tells Jekyll to build the website with production mode 
      (includes Google Analytics in our case).
2. Jekyll will build the website into the `_sites` directory
3. Upload the files in `_sites` to the `/mit/anz/web_scripts/` AFS locker on Athena. You can use rsync or scp for this.
    - Run `rsync -r _site/ athena.dialup.mit.edu:/mit/anz/web_scripts/`
4. Don't forget to commit your changes to Github!

Instructions for setting up access to Athena can be found here: https://web.mit.edu/dialup/www/ssh.html
