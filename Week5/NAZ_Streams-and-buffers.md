#### What is a stream?
* The stream is the flow of packets of data from one place to another. 
* The buffer dictates the size of the packets of data.

* Streaming allows the data to be transfered in smaller chunks, which is quicker and allows the client to use part of the data even when they haven't got the whole file
![Diagram of stream](https://i.imgur.com/VgRuKGR.png)

---
#### Why use streams??
![](https://i.imgur.com/1O91Lch.jpg)



---
examples of streams in action (Note **source.pipe(destination)**)
![](https://i.imgur.com/xm165U3.png)

---
Source.pipe(destination)
### Four types of streams:
* **Readable** (fs.createReadStream()) > Can act as the source, but not the destination
* **Writable** (fs.createWriteStream()) > Can act as the destinations, but not the source.
* **Duplex** - Both readable and writeable
* **Transform** - Duplex streams that can modify or transform the data as it is written and read (for example zlib.createDeflate()).

---

* 
Additionally this module includes the utility functions pipeline and finished.
#### What is a buffer?
A temporary storage spot of defined length that is being transferred from once place to another. Once each buffer fills it will be passed on to the end-point through the stream.
The buffer is useful for cituations where data is coming in too slow or too fast.

##### Data flow is too fast
If the rate the data arrives is faster than the rate the process consumes the data, the excess data need to wait somewhere for its turn to be processed.

##### Data flow is too slow
On the other hand, if the process is consuming the data faster than it arrives, the few data that arrive earlier need to wait for a certain amount of data to arrive before being sent out for processing.

JavaScript language had no mechanism for reading or manipulating streams of binary data. The Buffer class was introduced as part of the Node.js API to enable interaction with octet (a.k.a. 8 bits of binary) streams, file system operations, and other contexts. So, ultimately buffers hold a raw of binary data, and it does let us figute out how to switch between those zeros and ones and string assuming we are artoring a string information  
![Diagram of buffer](https://i.imgur.com/wA8tqoP.png)


### Further reading
What is a buffer & stream: 
https://medium.freecodecamp.org/do-you-want-a-better-understanding-of-buffer-in-node-js-check-this-out-2e29de2968e8

Node.js Docs on buffer: 
https://nodejs.org/dist/latest-v8.x/docs/api/buffer.html#buffer_buffer

Node.js Docs on stream: https://nodejs.org/api/stream.html
