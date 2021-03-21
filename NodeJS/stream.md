# Stream

## What Are Streams

**Streams** are data-handling method in which data is read _chunk by chunk_ (buffers). They are a way to handle reading/writing files, network communication, or any kind of end-to-end information exchange in an _efficient_ way.

  - Streams are **memory-efficient** : using streams, you can read data chunk by chunk, processing its content without keeping it all in memory
  - Streams are **time-efficient** : you can start processing data as soon as you have it, without waiting for the whole data to be available

## Readable Streams
- Readable streams allow Node.js to read data from a stream

- How to create a readable stream
  ```javascript
  const http = require('http');
  const fs = require('fs');

  const readStream = fs.createReadStream(__dirname + '/readdata.txt', 'utf8');

  readStream.on('data', (chunk) => {
    console.log('new chunk received');
    console.log(chunk);
  });
  ```

## Writable Streams
- Sritable streams allow Node.js to write data to a stream

- How to create a writable stream
  ```javascript
  const http = require('http');
  const fs = require('fs');

  const readStream = fs.createReadStream(__dirname + '/readdata.txt', 'utf8');
  const writeStream = fs.createWriteStream(__dirname + '/writedata.txt');

  readStream.on('data', (chunk) => {
    console.log('new chunk received');
    writeStream.write(chunk);
  });
  ```

cf. What is the difference between `fs.readFile` & `fs.writeFile` and `fs.createReadStream` & `fs.createWriteStream`? 

With `fs.readFile` and `fs.writeFile`, you need to wait for all of the data to be stored in the memory before process it. On the other hand, with `fs.createReadStream` and `fs.createWriteStream` you can start processing the data without waiting for the whole data to be available.