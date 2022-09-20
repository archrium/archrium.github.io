# Project Archrium
This is a World of Warcraft Guild website and experimentation project.

| Project Started | Last Update | Version |
| :-------------- | :---------- | :-----: | 
| 02-Sep-2022     | 20-Sep-2022 | 0.40    |
# Table of Contents
1. [Description](#description)
2. [Installation and Usage](#installation-and-usage)
3. [Controls](#controls)
4. [Feature List](#feature-list)
5. [Display](#display)
6. [References](#references)

# Description

# Installation and Use
- Installation
    - environment
        - install visual studio code 
        - install TypeScript Vue Plugin (Volar)
    - frameworks, libraries etc.
        - install **node**
        - get in project folder in your console `cd website`
        - nuxt 2:
            - install `npx create-nuxt-app <project-name>`
                - project name: archrium (lowercase node does not allow otherwise)
                - programming lang: JavaScript
                - package manager: Npm
                - ui framework: no
                - nuxt.js modules: content - git based headless cms
                - linting tools: prettier
                - testing framework: none
                - rendering mode: single page app
                - deployment target: server(node.js hosting)
                - development tools: jsconfig.json
                - git username: Archrium
                - version control system: git
            - install  npm install --save-dev @nuxtjs/color-mode@2.1.1
            - install `npm install --save-dev @nuxt/content@1.14.0`
            - create folder `discard`
                - move readme to discard
                - remove or merge gitignore 
                - remove .git folder in website
            - install `npm install prism-themes`
        - nuxt 3
            - install `npx nuxi init nuxt-app`
            - enter project folder then `npm install`
            - use development server `npm run dev -- -o`
            - install `npm install --save-dev @nuxtjs/color-mode`
            - install tailwind `npm install --save-dev @nuxtjs/tailwindcss@5.0.0-4`
- Use
    - get in folder `cd <website>`
    - to develop `npm run dev`
    - to package and publish `npm run generate`

# Controls

# Feature List
- [x] 18-Sep-2022 Adaptive Styling for different screen sizes
- [x] 13-Sep-2022 Data-view separation
    - [x] 13-Sep-2022 Import `json` content
    - [x] 13-Sep-2022 Import `markdown` content
- [x] 12-Sep-2022 Color Mode: dark/light/sepia themes

# Display

# References
- environment
- content
    - markdown test file by John Gruber
    - markdown test file (https://github.com/mxstbr/markdown-test-file)