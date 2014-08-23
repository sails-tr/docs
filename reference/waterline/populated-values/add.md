he file object, we can write:

	promiseForCompletion = file.write(contents, options, encoding);

To close the file object, we can write:

	promiseForCompletion = file.close();

We can also use file.writeSync and file.closeSync for the synchronous versions of these
functions.

The file object is also a lazy array, which means you can read from the file using 
standard array methods. To asynchronously read the contents of a file, you can do:
 
	file.forEach(function(chunk){
		// called for each chunk of the file until the end of the file is reached.
	});

# lazy-array

The lazy-array module provides the functionality for creating and using lazy arrays,
which are objects that implement the interface of the standard iterative array methods for accessing
streams of data. Array methods can be called and they will be
asynchronously executed as data is available. Lazy arrays are powerful way to model
asynchronous streams since they can used like other JavaScript arrays.

Typically you don't need to directly use this module, rather other IO modules like the 
file system (fs) and HTTP (http-client) modules provide lazy arrays that you can interact
with. For example, we could search through a file for the string "lazy" and stop reading
once we find it using the standard some() method:

	if(file.some(function(chunk){
		return chunk.toString().indexOf("lazy") > -1;
	}));

Lazy arrays include the follow standard array methods, providing access to the data
as the stream data becomes available:

* filter
* every
* some
* forEach
* concat
* map

And also these standard methods, although these must fully fetch the stream:

* join
* sort
* reverse

Also the following additional methods are available on lazy arrays:

* toRealArray() - This will fetch all the data and return it as a real JavaScript array.
* get(index) - This retrieves an element by