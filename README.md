# BashTemplate

BashTemplate is a simple bash template engine and runner for Node.js.

## Installation

```
$ npm install node-bash-template --save
```

## Usage

`/bash/script.sh`

```bash
echo {{message}}
```

`/index.js`

```javascript
// core deps
var
    path = require('path');

// module deps
var
    BashTemplate = require('node-bash-template');

var
    options = {
        template: {
            dir: path.resolve(__dirname, './bash'),
            ext: 'sh'
        }
    },
    template = BashTemplate.forge(options);

console.log(template.render('script', { message: 'ok' })); // echo ok\n

template.run('script', { message: 'ok' }, function (error, stdout, stderr) {
    if (error) {
        throw error;
    }

    console.log(stdout); // ok\n
    console.log(stderr); // 
});
```

## License

The project is licensed under the MIT license.
