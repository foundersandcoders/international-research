# Streams and Buffers
* Research what streams and buffers are in Node, how are they used in conjunction?
* Create a Node project that lets a user run the command node bigtextfile.txt in the same directory as bigtextfile.txt and stream the contents of the file to the users terminal. Need a big file? How about a book.
* (Bonus) Allow an additional argument to be provided in the command to specify a time interval of how often a chunk of text from the file is streamed to the terminal. E.G node bigtextfile.txt 1s

## Overview

### Buffers

In computer science, a **buffer** is a space in memory that is used to store data temporarily, for example when moving data from one place to another.

* copying a file
* saving data recorded by a microphone
* sending data to a printer

When buffers are implemented in software, RAM is typically used to store the buffer as it has a much faster access time than the hard drive.

Buffers operate a FIFO algorithm - **First In, First Out**, also known as a queue.



This means that buffers are useful when transfering data between two devices that process data at different speeds.
* e.g. from a hard drive, which has a limited access rate, to a speaker, which can execute incoming data at a faster rate

### Streams

**Streams** differ from buffers in the way they consume data chunks.

Streams can read and write data **chunk by chunk**, without buffering the whole file at once. Streams often use buffers to optimise data transmission speed.

There are different types of streams in Node.js:

* **readable** streams
* **writable** streams
* **duplex** streams

Streams also emit **events**, such as `data`, `error`, `end` and `finish`, as they process chunks.

## Buffers (Artemis)

**The basics**
* `Buffer` is a Node module with umpteen properties and methods (and whoever does not behave will have to write them out all 100 times).

![](https://i.imgur.com/uXkfN2W.jpg)

Here's how the [Node.js documentation](https://nodejs.org/dist/latest-v8.x/docs/api/buffer.html#buffer_buffer) defines it:

![](https://i.imgur.com/FXnmf5Y.jpg)

Huh???

![](https://i.imgur.com/gnfDFN9.jpg)

Exactly. The 'official' definition looks undecipherable at first (and second) glance. to understand buffers, we need a bit of background.

**Encoding and decoding data**
Computers deal with a variety of data: numbers, strings, images, audio, video. Garden-variety (as opposed to quantum- variety) computers translate all data to a  predefined number, then this number into a binary entity - they encode data into binaries and decode the latter back into data. A sequence of data forms a stream that the computer takes from one point to another point - e.g. from a text editor application to a printer.

However, computers cannot handle unlimited amounts of data, so if the data arriving from point A cannot be channeled all at once to point B, they'll have to queue up in a sort of waiting area in the computer's memory. 

![](https://i.imgur.com/gkziXuM.jpg)

A buffer is a physical location in a computer's RAM where data queue up and wait to be processed. The `Buffer` methods Node.js uses are ways of manipulating the buffer.

Choppy video streams are a typical example of what happens in the `Buffer` area when data trickles in when the Internet connection is slow: the computer processes chunks of data faster than they arrive, which means that when the first chunk is processed (i.e. displayed), the buffer is left empty until the next chunk is there in its entirety and the buffer fills up. Think of it as a group travelling together; the group won't be moved on to the next location until everyone is there.

 **Node.js `Buffer` methods**
 Node.js creates a buffer automatically when data are streamed; however, we can also create custom buffers.

//*Use the `alloc` method to create an empty Buffer of specified length.*

    `const buff = Buffer.alloc(25);`

//*Create buffer and place some content in it*

    `const buffFromString = Buffer.from('Put some text in the buffer');`

**Things to note**
* `Buffer` is a global object and does *not* need to be imported with `require`.
* The methods that have replaced the now deprecated `new Buffer()` constructor are `Buffer.from()`, `Buffer.alloc()` and `Buffer.allocUnsafe()`. The difference between the `Buffer.alloc()` and `Buffer.allocUnsafe()` methods is that the 'unsafe' buffer may create data from older buffers. A buffer created with `Buffer.allocUnsafe(size)` represents *uninitialised* memory, which may contain data from older buffers. These data need to be completely overwritten.

**Sources**
* https://nodejs.org/dist/latest-v8.x/docs/api/buffer.html#buffer_buffer
* https://www.w3schools.com/nodejs/ref_buffer.asp
* https://medium.freecodecamp.org/do-you-want-a-better-understanding-of-buffer-in-node-js-check-this-out-2e29de2968e8

## Stream

Streams are objects which allow you to read data from a source or write data to a destination

Streams return smaller parts of the data (using the buffer) and trigger a callback when new data is available

The benefits of streams are that they provide a way to read or write data in chunks
* rather than reading a large file into memory and processing it all at once, you can stream the data into more managable sizes
* an example is reading data from a network and writing to a file as you receive it (don't have to wait for all the data until you dump it from memory to disk)


### Readable Streams

* readable streams let you read data from a source
* http.ServerRequest is a readable stream example

Readable streams emit the following events:
* Event: data - emits when the stream passes data to user
* Event: end - emitted when no more data events to be consumed
* Event: error - emits if there was an error receiving the data
### Writable Streams

* writable streams let you write to a destination
* http.ServerResponse is a writable stream example

Writable streams emit the following events:
* Event: drain - signal that the writable stream can receive more data
* Event: finish - when all data has been flushed, finish is emitted
* Event: error - emitted on error



### Project
Chunking Shakespeare
```
const fs = require("fs");
if (process.argv.length === 4) {
  var delay = process.argv[3].split("s")[0] * 1000;
}

var readStream = fs.createReadStream(process.argv[2], "UTF8");

readStream.on("data", function(chunk) {
  console.log(chunk);
  if (delay) {
    readStream.pause();
    setTimeout(() => {
      readStream.resume();
    }, delay);
  }
});
```
