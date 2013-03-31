# avconv

simply spawns an avconv process with any parameters and returns the result to you. very small, fast, clean and does only this.

## installation
    
to install find-delete, use [npm](http://github.com/isaacs/npm):

    $ npm install avconv
    
then in your node.js app, get reference to the function like that:
    
```javascript
var avconv = require('avconv');
```

## quick example

### make an avi video out of images

```javascript
var params = [
    '-f', 'image2',
    '-loglevel', 'info',
    '-i', '/tmp/images/',
    '-y', '/tmp/output.avi'
];

avconv(params, callback);
```

(avconv consultation is not subject of this module. if you need help with parameters, have a look at http://libav.org/avconv.html)

### callback(code, stdout, stderr)

three parameters are always passed onto the callback:

```
function callback(code, stdout, stderr) {
    // add your logic here
}
```

code = 0 (zero) means there was no problem. an exit code of 127 means the program avconv could not be found. i recommend you to use a switch block to deal with these error codes.

stdout might contain any useful information, depending on the log level. stderr will have any warnings or error information in case of a problem.

## api

### avconv(params, callback)

avconv spawns a new avconv process with any given parameters. it does not validate the parameter nor the results. that's all up to you.
 
__arguments__

* params - any array list with string arguments
* callback - the callback function to be called when process is finished. it passes three parameters:
    * code - any integer where 0 means OK. anything above 0 indicates a problem (exit code).
    * stdout - a string with useful information, depending on the log level.
    * stderr - a string with potential warnings or errors.

## license

MIT