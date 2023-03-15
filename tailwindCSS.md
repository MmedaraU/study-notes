# References
> [Tailwind Docs](www.tailwindcss.com)


# Tailwind Setup (v3.2)
Needs an internet connection and is done for every project.

1. Install tailwindCSS and initialize repo  
    ```
    npm install -D tailwindcss
    npx talwindcss init
    ```

2. In `src` folder, create an `(input).css` file and put the build commands
    ```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```

3. In the `tailwind.config.js`, add the paths to the files in the src folder to the `content` array  
    `content: [".src/input.css"]`



4. In `dist` or `public` where the actual code will be generated, create the `style.css` and `index.html` files

<!-- 5. Add to the `package.json` file, in the script section after clearing existing content
    ```json
    "scripts": {
      "build:css": "tailwind build src/input.css -o dist/style.css"
    }
    // -o stands for output
    // built from src and generated in dist folder
    ``` -->

<!-- 6. Run command in the terminal  
    `npm run build:css`  
    In the dist folder, the tailwindCSS styles will be generated. Tailwind uses `normalize.css` for its reset. -->

5. Run the command  
    `npx tailwindcss -i ./src/input.css -o ./dist/style.css --watch`

6. Add css link to html  
    `<link href="/dist/style.scss" rel="stylesheet">`


# Upgrade version 
`npm install -D tailwindcss@latest postcss@latest autoprefixer@latest`

# Create Custom Styles
You have to use the `tailwind.config.js` file. You can change breakpoint, create  custom colors, change font-families, can set default container styles, etc.

1. Run the command   
`npx tailwind init`

2. After running the command, run the `npm run build:css`