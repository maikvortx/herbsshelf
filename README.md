 <p align='center'><img src='https://avatars3.githubusercontent.com/u/60399865' height='220'></p>

![CI build](https://github.com/herbsjs/herbsshelf/workflows/CI%20build/badge.svg) [![codecov](https://codecov.io/gh/herbsjs/herbsshelf/branch/main/graph/badge.svg)](https://codecov.io/gh/herbsjs/herbsshelf)

# herbsshelf

Welcome to the shelf!

This is a self-generate documentation, here you can see all the flow of information in the application.

You can use the lateral panel to navigate into Use Cases of this application. 

 <p align='center'><img src='docs/herbs_shelf.png' height='440'></p>

### Installing
```
    $ npm install @herbsjs/herbsshelf
```

### Functioning 

To use the shelf you will need to pass a list of usecases to it, it will read them and return a string from an HTML document with the generated documentation.

### Using 

The quickest way to use the herbs shelf is to create a rest route in your api and expose the documentation generated by the shelf.

Consider a file called _uclist.js with this inside
```javascript


module.exports = (injection) => {
    return [
        { usecase: require('./myUseCaseFile').myUseCaseName(injection), tags: { group: 'GroupOne' } },
        { usecase: require('./myUseCase2File').myUseCase2Name(injection), tags: { group: 'GroupOne' } },
        { usecase: require('./myUseCase3File').myUseCase3Name(injection), tags: { group: 'GroupTwo' } },
    ]
}
```

In your app or server file, import the shelf dependecy and the list of usecases

```javascript

const usecases = require('../../domain/usecases/_uclist')
const renderShelfHTML = require('herbsshelf')


```

And call the shelf into you prefered rest route

```javascript

 this.app.get('/herbsshelf', (req, res, next) => {
    res.setHeader('Content-Type', 'text/html')
    const shelf = renderShelfHTML('Project Name', usecases())
    res.write(shelf)
    res.end()
})

```

If your project has a `readme.md`, this content should be shown at the beginning of the project. If you want to use a custom readme, you can specify on startup:

```javascript

const shelf = renderShelfHTML('Project Name', usecases(), './custom-readme.md')

```


You can see the full functionality into the [TODO-LIST ON HERBS repository](https://github.com/herbsjs/todolist-on-herbs)

## TODO

- [X] Self-documentation
- [ ] Add templates and injection of css file
- [X] Entities of gotu support
- [ ] Playground functionality
- [ ] GraphQL documentation sample


### Contribute
Come with us to make an awesome *herbsshelf*.

Now, if you do not have the technical knowledge and also have intended to help us, do not feel shy, [click here](https://github.com/herbsjs/herbsshelf/issues) to open an issue and collaborate their ideas, the contribution may be a criticism or a compliment (why not?)

If you would like to help contribute to this repository, please see [CONTRIBUTING](https://github.com/herbsjs/herbsshelf/blob/main/.github/CONTRIBUTING.md)

### License

**herbsshelf** is released under the
[MIT license](https://github.com/herbsjs/herbsshelf/blob/main/LICENSE.md)