[![Build Status](https://travis-ci.org/telemark/generate-docx.svg?branch=master)](https://travis-ci.org/telemark/generate-docx)
[![Coverage Status](https://coveralls.io/repos/telemark/generate-docx/badge.svg?branch=master&service=github)](https://coveralls.io/github/telemarks/generate-docx?branch=master)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/feross/standard)

# generate-docx

Generates .docx from [template](test/data/testdoc.docx) and [data](test/data/testdata.json)

Returns a Buffer or saves the generated file if given path and filename.

## Example save file

### Promises

```js
const generateDocx = require('generate-docx')

const options = {
  template: {
    filePath: 'test/data/testdoc.docx',
    data: {
      title: 'This is the title',
      description: 'Description is good',
      body: 'My body is my temple'
    }
  },
  save: {
    filePath: 'test/data/savedfile.docx'
  }
}

generateDocx(options)
  .then(console.log)
  .catch(console.error)
```

### Callback

```js
const generateDocx = require('generate-docx')

const options = {
  template: {
    filePath: 'test/data/testdoc.docx',
    data: {
      title: 'This is the title',
      description: 'Description is good',
      body: 'My body is my temple'
    }
  },
  save: {
    filePath: 'test/data/savedfile.docx'
  }
}

generateDocx(options, (error, message) => {
  if (error) {
    console.error(error)
  } else {
    console.log(message)
  }
})
```

## Example return buffer

### Promises

```js
const { writeFileSync } = require('fs')
const generateDocx = require('generate-docx')

const options = {
  template: {
    filePath: 'test/data/testdoc.docx',
    data: {
      title: 'This is the title',
      description: 'Description is good',
      body: 'My body is my temple'
    }
  }
}

generateDocx(options)
  .then(buf => {
    writeFileSync('test/data/frombuffer.docx', buf)
    console.log('File written')
  }).catch(console.error)
```

### Callback

```js

const { writeFileSync } = require('fs')
const generateDocx = require('generate-docx')

const options = {
  template: {
    filePath: 'test/data/testdoc.docx',
    data: {
      title: 'This is the title',
      description: 'Description is good',
      body: 'My body is my temple'
    }
  }
}

generateDocx(options, (error, buf) => {
  if (error) {
    console.error(error)
  } else {
    writeFileSync('test/data/frombuffer.docx', buf)
    console.log('File written')
  }
})
```

## License

[MIT](LICENSE)

![Robohash image of generate-docx](https://robots.kebabstudios.party/generate-docx.png "Robohash image of generate-docx")
