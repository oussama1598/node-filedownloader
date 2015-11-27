# node-filedownloader
makes downloading very easy

## Quick start
```sh
    npm install filedownloader
```
Then:
```javascript
    var Downloader = require("filedownloader");
    
    var Dl = new Downloader({
        url: "FILEURL"
    }).on("progress", function (progress){
        console.log(progress); 
    });
```
The progress event will return :
```js
    { progress: '1.3', dataWritten: 376072, filesize: '29828970' } //just an example of the ouput
```

### Controlling The Download
you can pause the downloading by :
```js
    Dl.pause();
```
and you can resume it by:
```js
    Dl.resume();
```
### Setting event handlers
#### 'start': download started
    The `start` event is emitted just after the download starts
    
```js
    Dl.on("start", function(){
       console.log("Download started") 
    });
```
#### 'progress': progress information
    It is emitted with an object argument with the following keys:
    
    * `dataWritten`: size of downloaded data in bytes
    * `filesize`: size of the target file in bytes
    * `progress`: an estimation of the progress percentage

```js
    Dl.on("progress", function(progress){
       console.log('Downloaded: ' + progress.percent + '%); 
    });
```
#### 'error': error occurred
    The `error` event is emitted when an error occurs
```js
    Dl.on("error", function(err){
       console.log('Some error occurred:' + err); 
    });
```
#### 'end': Downloading finished
    The `end` event is emitted when Downloading has finished.
    
```js
    Dl.on("end", function(){
       console.log('Download finished'); 
    });
```    
## Tests

```sh
npm test
```

## Dependencies

- [mkdirp](https://github.com/substack/node-mkdirp): Recursively mkdir, like `mkdir -p`
- [urlencode](https://github.com/node-modules/urlencode): encodeURIComponent with charset
- [valid-url](https://github.com/ogt/valid-url): URI validation functions

## License

GPL-3.0