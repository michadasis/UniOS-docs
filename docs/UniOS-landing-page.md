# UniOS Landing Page

## Description
 UniOS Landing Page is a webpage about UniOS, an operating system designed specifically for university students. It contains information about the apps included, the members of the team who created it and some frequently asked questions about it. Moreover, visitors can download the ISO of UniOS and visit the project's documentation website. It's purpose is to familiarize visitors with UniOS.

## Installation guide
### As a user
Because is a webpage, users don't have to install it. If they want to visit this landing page, they can click here: https://unios-project.eu

### As a developer
As a developer, you have to follow these steps:
- Make a fork of this repository.
- Clone your fork locally.
- Run the project with this command:

    `python3 -m http.server 8000`

    _Note: To run this command, you need to have python installed._ 


## Project structure 
The structure of the project is this: 
 ```bash
.
├── assets
│   ├── css
│   ├── fonts
│   ├── images
│   ├── js
│   ├── logo
│   ├── members
│   └── mockup
├── index.html
├── LICENSE
├── locales
├── README.md
└── vendor
    ├── bootstrap
    └── jquery
 ```

## How to modify this project
- To change the html code, modify the index.html.
- To change the css code, modify the unios_theme.css file.
- To modify the webpage's text, first edit the values in 'en.json' and 'el.json', which are the webpage’s translation dictionaries, and then update the corresponding HTML elements. These dictionaries are located in the locales folder. 'en.json' contains the English text, and 'el.json' contains the Greek text.
- To add text to the webpage, you have to follow these steps:
    - Add a key-value pair to both el.json and en.json, with the new text in Greek and English respectively. For instance: 

       - en.json:  `"your_translation_key" : "text in english",`
       - el.json: `"your_translation_key" : "text in greek",`
    - Add the data-i18n attribute to the HTML element containing this text, and set it to the corresponding key. For example: 

        `<element data-i18n="your_translation_key">...</element>`
    - Add your text to the corresponding html element, for backup. 

## Contributing
Contributions are welcome. If you want to improve the UI, fix a typo, or add a new page, open a pull request on GitHub. If you find a bug, open an issue. There is no contribution too small.

Built by Open Source UoM 2026
