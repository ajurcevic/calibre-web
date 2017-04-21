   ![Version](https://img.shields.io/badge/Library-2.1-blue.svg) 

# About

Calibre Web is a web app providing a clean interface for browsing, reading and downloading eBooks using an existing [Calibre](https://calibre-ebook.com) database.

*This software is a fork of [library](https://github.com/janeczku/calibre-web) and licensed under the GPL v3 License.*

![screenshot](https://raw.githubusercontent.com/janeczku/docker-calibre-web/master/screenshot.png)

## Features

- Bootstrap 3 HTML5 interface
- full graphical setup
- User management
- Admin interface
- User Interface in english, french, german, polish, simplified chinese, spanish
- OPDS feed for eBook reader apps 
- Filter and search by titles, authors, tags, series and language
- Create custom book collection (shelves)
- Support for editing eBook metadata
- Support for converting eBooks from EPUB to Kindle format (mobi/azw)
- Restrict eBook download to logged-in users
- Support for public user registration
- Send eBooks to Kindle devices with the click of a button
- Support for reading eBooks directly in the browser (.txt, .epub, .pdf)
- Upload new books in PDF, epub, fb2 format
- Support for Calibre custom columns
- Fine grained per-user permissions
- Self update capability


## Adding Google Drive integration

Additional optional dependencys are necessary to get this work. Please install all optional  requirements by executing `pip install -r optional-requirements.txt`

To use google drive integration, you have to use the google developer console to create a new app. https://console.developers.google.com

Once a project has been created, we need to create a client ID and a client secret that will be used to enable the OAuth request with google, and enable the Drive API. To do this, follow the steps below: -

1. Open project in developer console
2. Click Enable API, and enable google drive
3. Now on the sidebar, click Credentials
4. Click Create Credentials and OAuth Client ID
5. Select Web Application and then next
6. Give the Credentials a name and enter your callback, which will be CALIBRE_WEB_URL/gdrive/callback
7. Finally click save

The Drive API should now be setup and ready to use, so we need to integrate it into Calibre Web. This is done as below: -

1. Open config page
2. Enter the location that will be used to store the metadata.db file, and to temporary store uploaded books and other temporary files for upload
2. Tick Use Google Drive
3. Enter Client Secret and Client Key as provided via previous steps
4. Enter the folder that is the root of your calibre library
5. Enter base URL for calibre (used for google callbacks)
6 Now select Authenticate Google Drive
7. This should redirect you to google to allow it top use your Drive, and then redirect you back to the config page
8. Google Drive should now be connected and be used to get images and download Epubs. The metadata.db is stored in the calibre library location
