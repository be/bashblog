bashblog
========

A single Bash script to create blogs. 

I created it because I wanted a very, very simple way to post entries to a blog by using a public folder on my server, without any special requirements and dependencies. Works on GNU/Linux, OSX and BSD.

You can see it live here: [read the initial blog post](http://mmb.pcb.ub.es/~carlesfe/blog/creating-a-simple-blog-system-with-a-500-line-bash-script.html). My blog has been 100% generated using bashblog, no additional tweaking.


Features
--------

- No installation required. Download `bb.sh` and start blogging.
- Ultra simple usage: Just type a post with your favorite editor and the script does the rest. No templating.
- All content is static. You only need shell access to a machine with a public web folder.
  *Tip: advanced users could mount a remote public folder via `ftpfs` and run this script locally*
- Allows drafts, includes a simple but clean stylesheet, generates the RSS file automatically.
- Support for Markdown, Disqus comments, Twitter, Feedburner, Google Analytics.
- GNU/Linux, BSD and OSX compatible out of the box (no need for GNU `coreutils` on a Mac)
- Everything stored in a single 700-line bash script, how cool is that?! ;) 


Usage
-----

Copy bb.sh into a public folder (for example, `$HOME/public_html/blog`) and run

    ./bb.sh

This will show the available commands. If the file is not executable, you can either `chmod +x bb.sh`
or run it with `bash bb.sh`

**Before creating your first post, you may want to configure the blog settings (title, author, etc).
Read the Configuration section below for more information**

To create your first post, just run:

    ./bb.sh post

When you're done, access the public URL for that folder  (e.g. `http://server.com/~username/blog`) 
and you should see the index file and a new page for that post!


Configuration
-------------

Configuration is not required for a test drive, but if you plan on running your blog with bashblog, you will
want to change the default titles, author names, etc, to match your own.

There are two ways to configure the blog strings:

- Edit `bb.sh` and modify the variables in the `global_variables()` function
- Create a `.config` file with your configuration values (useful if you don't want to touch the script)

The software will load the values in the script first, then overwrite them with the values in the `.config` file.
This means that you don't need to define all variables in the config file, only those which you need to override
from the defaults.

The format of the `.config` file is just one `variablename="value"` per line, just like in the `global_variables()`
function. **Please remember:** quote the values, do not declare a variable with the dollar sign, do not use 
spaces around the equal sign.

bashblog uses the `$EDITOR` environment value to open the text editor.


Detailed features
-----------------

- A simple but nice and readable design, with nothing but the blog posts
- **NEW on 2.0** Markdown support via a third-party library (e.g. 
  [Markdown.pl](http://daringfireball.net/projects/markdown/)). Use
  it via `./bb.sh post -m`. The third party library must support an invokation
  like `markdown_bin in.html > out.md` as the code calls it that way.
- Post preview
- Save posts as drafts and resume editing later
- HTML page for each post, using its title as the URL
- Configurable number of posts on the front page
- Automatic generation of an RSS file, feedburner support
- Additional page containing an index of all posts
- Rebuild all files while keeping the original data
- Comments delegated to Twitter, with additional Disqus support
- Google Analytics code support
- Contains its own CSS so that everything is reasonably styled by default
- Headers, footers, and in general everything that a well-structured html file needs
- Support to add extra content on top of every page (e.g. banners, images, etc)
- xhtml validation, CSS validation, RSS validation by the w3c
- Automatic backup of the site every time you post (stored as `.backup.tar.gz`)

Read the CHANGELOG section of the script header for more updates
