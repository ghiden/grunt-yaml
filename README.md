# grunt-yaml [![Build Status](https://secure.travis-ci.org/shiwano/grunt-yaml.png?branch=master)](http://travis-ci.org/shiwano/grunt-yaml)

This is a fork of original grunt-yaml https://github.com/shiwano/grunt-yaml

Only chage that I made is middleware.

It takes a function that takes a yaml-parsed JSON object.
This is for when you want to tweak this JSON object before it gets stringified.
In this function, do whatever you need to do and return the modified object.

## The "yaml" task

### Middleware

To manipulate the data on your own, provide a middleware function and return the manupulated response for serializing to JSON:

```js
grunt.initConfig({
  yaml: {
    your_target: {
      options: {
        middleware: function(response){
            // do something with JSON object
            return response
        },
        space: 4
      },
      files: {
        'config.json': ['config.yml']
      }
    },
  },
})
```

### Options

#### options.middleware
Type: `function`
Default value: `function(response){ return response; }`

A function which provides you an interface to manipulate the yaml-parsed JSON object before it gets stringified into JSON.

