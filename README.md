## astroturf-loader

A distinct package for the astroturf webpack integration

## Install

```
npm install astroturf astroturf-loader
```

## Basic configuration

This is all the webpack setup necessary:

```js noFormat
{
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.jsx?$/,
        use: ['babel-loader', 'astroturf-loader'],
      },
    ],
  }
}
```

Add the `astroturf-loader` to the end of your JavaScript or TypeScript loader
chain and you are ready to get compilin'!

If you want to use astroturf with a CSS preprocessor, just tweak an option to output
the file type of your choice. Here's an example using Sass:

```js noFormat
{
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: ['style-loader', 'css-loader', 'sass-loader'],
      },
      {
        test: /\.jsx?$/,
        use: [
          'babel-loader',
          {
            loader: 'astroturf-loader',
            options: { extension: '.module.scss' },
          },
        ],
      },
    ],
  }
}
```

Becauase astroturf outputs CSS modules, it's best to use a `.module.*` extension. This
automatically tells webpack's `css-loader` to process the stlyes correctly and expose the
class names as exports for JS files. You can use whatever extension you like though, but
may need to manually configure CSS modules elsewhere.

Consult the astroturf docs for more details on individual options
