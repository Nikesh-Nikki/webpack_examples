# Webpack Code Examples

---

## Basic JS bundling :

On main branch, we have index.html (directly in dist folder) it includes script bundle.js.

Now we write index.js that imports a package loadash.

We install webpack webpack-cli using `npm install webpack webpack-cli --save-dev`

Then, we give webpack an entry point and a location for the destination bundle (which in our case is dist folder)

Run `npx webpack` and you will see that bundle.js is created in dist folder.

Now try opening index.html.

## Assets :

On assets branch, there is a style.css file and an image in src folder. 

we import css file in index.js

Webpack doesnt know how to bundle css files. So we use loaders : css-loader and style-loader

We then let webpack know that it should use these loaders for css files.

For images, If there is `url('myimage.png')` in css File. myimage.png will be added to dist.

## React : 

We obviously import react and reactdom to index.js.

Then we create root and render it with simple html.

webpack doesnt know how to compile jsx.

So we install babel/core , babel/present-env , babel/present-react , babel-loader packages by running 

`npm install --save-dev @babel/core @babel/preset-env \@babel/preset-react babel-loader`

We will add babel loader to webpack.config.js

    module: {
      rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ['babel-loader']
      }
      ]
    },

We then set babel presets by creating `.babelrc` in root directory. Then write : 

    {
      "presets": [
      "@babel/preset-env",
        "@babel/preset-react"
      ]
    }

Then run `npx webpack` and open index.html.

For more info about how to add ESLint, prettier and more checkout : 
<https://www.freecodecamp.org/news/how-to-set-up-deploy-your-react-app-from-scratch-using-webpack-and-babel-a669891033d4/>
