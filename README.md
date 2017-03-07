# Directory Theme
A simple, customizable theme for your **Apache** or **nginx** directory listing.
Here is a demo of what the result looks like: [gif library](http://gifs.jessfraz.com).

**Features**

- search the directory and display results, as the user inputs the search term
- custom styling of the default directory indexing
- ```.html``` files are linked to without the file extension (ex. http://localhost/example.html -> http://localhost/example)
- changes "Last modified" column to display time as time since (ex. 2 minutes ago, 4 days ago, etc)

**Apache Features**

## Apache Setup
Be sure you have ```mod_autoindex``` loaded on your server.

```bash
$ cd into_vhost_root_directory_you_want_to_be_prettified/
$ git clone git@github.com:lisogallo/directory-theme.git

# move the directory contents to the parent directory
$ cd directory-theme/
$ mv * .[^.]* ..
# you may get an output of: mv: cannot stat ‘*’: No such file or directory
# that's fine, if you `ls -a` the directory it should be empty
$ cd ../

# remove nginx items & .git just so it doesn't mess with your other stuff
$ rm -rf directory-theme.conf
$ rm -rf .git*
```

## nginx Setup
Be sure you have [```ngx_http_addition_module```](http://nginx.org/en/docs/http/ngx_http_addition_module.html) loaded on your server.

```bash
$ cd into_vhost_root_directory_you_want_to_be_prettified/
$ git clone git@github.com:lisogallo/directory-theme.git

# move the directory contents to the parent directory
$ cd directory-theme/
$ mv * .[^.]* ..
# you may get an output of: mv: cannot stat ‘*’: No such file or directory
# that's fine, if you `ls -a` the directory it should be empty
$ cd ../

# remove apache items & .git just so it doesn't mess with your other stuff
$ rm -rf .htaccess
$ rm -rf .git*

# rename directory-theme.conf to your site config name
# at the same time moving it to the sites-available folder
$ sudo mv directory-theme.conf /etc/nginx/sites-available/site.conf

# edit the relevant fields for your setup
# these are server_name and root
$ sudo vim /etc/nginx/sites-available/site.conf

# activate the host by creating a symbolic link between
# the sites-available directory and the sites-enabled directory
$ sudo ln -s /etc/nginx/sites-available/site.conf /etc/nginx/sites-enabled/site.conf

# restart nginx
$ sudo service nginx restart
```

### Credits
Based on [directory-theme](https://github.com/jessfraz/directory-theme) by Jess Frazelle, which is based on [apaxy](https://github.com/AdamWhitcroft/Apaxy) by Adam Whitcroft
