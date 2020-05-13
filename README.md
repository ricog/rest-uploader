# rest-uploader
REST API File Uploader for Joplin

[API Reference](https://joplin.cozic.net/api/)

Joplin client will need Webclipper service enabled.
* Go to Tools -> Web Clipper Options -> Enable Web Clipper Service


### Tesseract
In order for OCR text recognition to work, you'll need to download and
install Tesseract. Windows systems may require that you add a path variable
in order for it to work.

### Poppler
Poppler is required for PDF processing.
For Windows, download x86 binary and add to environment path.
https://blog.alivate.com.au/poppler-windows/


### Running application
Launch using the executable rest_uploader, specify the monitoring path
as an argument. You'll need your Joplin API key the first time you
launch. If your API key changes or gets pasted incorrectly, delete the .api_token.txt file that gets stored to the package.

` rest_uploader /path/to/directory `

To launch as python module:

` python -m rest_uploader.cli /path/to/directory `

### Languages other than English
Version 0.4.0 added language support via Tesseract (check Tesseract docs). To enable, use the cli -l or --language argument.
The following example will OCR text using the German dictionary:
` rest_uploader /path/to/directory --language ger `

### Additional Command Line Options added in version 1.8.0
By default notes will be dropped into a notebook called "inbox".
Specify a different upload notebook by specifying a destination from the
command line using -d or --destination

rest_uploader will fail if the specified notebook does not exist
I am guessing if you have two notebooks with the same name, it will dump
new notes in the first one it finds.

Default server = 127.0.0.1
To specify a different server, use the -s or --server cli option

Default port = 41184
To specify a different port, use the -p or --port cli option

It doesn't matter if the options are before or after the path. Path is mandatory, though.
The following example will upload newly created notes to the Taxes Notebook, and disable autotagging:
` rest_uploader -d "Taxes" -t no /path/to/directory `
