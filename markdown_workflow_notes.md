# markdown workflow for taking notes

## markdown file protocol
.md files are written in `nano`, `micro`, `vim` or `code`

# title of the document
```
# title of the document
```

## subtitle with underline
```
## subtitle with underline
```

### section
```
### section
```




important words are written in **bold** 

```
important words are written in **bold**
```

links can be references like so
[link](www.google.com)

```
[link](www.google.com)
```




with [scrot](https://github.com/resurrecting-open-source-projects/scrot), partial printscreens can be taken and referenced.
```
$ scrot -s /images/image.jpg 
```

images can be referenced like so 
![image](./images/a.jpg)


```
![image](./images/a.jpg)
```

inline `code` blocks are with backticks 
<pre><code>`code`</code></pre>

outline code blocks are with html tags or with triple backticks
```
<pre>
	<code>
	for(int i = 0; i< array.length; i++){
		console.log(i)
	}
	</code>
</pre>
``` 
<pre><code>
```
for(int i = 0; i< array.length; i++){
	console.log(i)
}
```
</code></pre>


## render markdown files

Use grip to create a live server that can render markdown files.

[grip source](https://github.com/joeyespo/grip/blob/master/tests/input/github.md)


```
$ grip -b notes.md 
```
for rendering multiple files, add a port number . 
```
$ grip -b notes.md 5192 
```

change the styling of all md files by changing the custom.css file 

```
$ micro ~/.grip/cache-4.2.0/custom.css 

```

reload qutebrowser to see the difference.
```
:reload -f
```
see the custom stylesheet in qutebrowser by the `:inspector` command