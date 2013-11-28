About this file
===============

A place for notes for myself on hacks to Octopress, Jekyll, etc.


Key Use Cases
--------------

### Create new post

    rake new_post["title"]

### Run a server that I can preview stuff with

    rake preview

### Prep for deploy

    git add ...
    git commit -m 'asdf'
    git push origin source

### Deploy to the interwebs

    rake gen_deploy

Joe's Changelog
===============

1200x167 =header



rake clean                     # Clean out caches: .pygments-cache, .gist-cache, .sass-cache
rake copydot[source,dest]      # copy dot files for deployment
rake deploy                    # Default deploy task
rake gen_deploy                # Generate website and deploy
rake generate                  # Generate jekyll site
rake install[theme]            # Initial setup for Octopress: copies the default theme into the path of Jekyll's generator.
rake integrate                 # Move all stashed posts back into the posts directory, ready for site generation.
rake isolate[filename]         # Move all other posts than the one currently being worked on to a temporary stash location (stash) so rege...
rake list                      # list tasks
rake new_page[filename]        # Create a new page in source/(filename)/index.markdown
rake new_post[title]           # Begin a new post in source/_posts
rake preview                   # preview the site in a web browser
rake push                      # deploy public directory to github pages
rake rsync                     # Deploy website via rsync
rake set_root_dir[dir]         # Update configurations to support publishing to root or sub directory
rake setup_github_pages[repo]  # Set up _deploy folder and deploy branch for Github Pages deployment
rake update_source[theme]      # Move source to source.old, install source theme updates, replace source/_includes/navigation.html with so...
rake update_style[theme]       # Move sass to sass.old, install sass theme updates, replace sass/custom with sass.old/custom
rake watch                     # Watch the site and regenerate when it changes
