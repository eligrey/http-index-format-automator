To have comments in directories, place a file named index.info file in a directory to show comments
in the generated application/http-index-format file

To have php-parsed comments in directories, place a file named index.info.php in a directory and start
every new line (not including first line) with '101: ' (without quotes)


Instalation
-----------
First, add this to an .htaccess file to make .info files viewable as plain text for non-Gecko browsers viewing directories and enable index viewing and RewriteEngine:


    AddType text/plain .info
    Options +Indexes
    RewriteEngine On



Depending on if you want certain index pages for directories, pick a following code to add to your .htaccess file


Make all directories, no matter what files are in them, to show a application/http-index-format file or the default index view page.

    RewriteCond %{HTTP:User-Agent} Gecko/
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule .* /http-index-format_automator.php?dir=%{REQUEST_FILENAME} [L,QSA]

Make all directories, except ones with a certain file (normally index.html or index.php) to show a application/http-index-format file or default index view page. Replace `FILENAME.EXT` with the index file name.


    RewriteCond %{HTTP:User-Agent} Gecko/
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteCond %{REQUEST_FILENAME}/FILENAME.EXT !-f
    RewriteRule .* /http-index-format_automator.php?dir=%{REQUEST_FILENAME} [L,QSA]
