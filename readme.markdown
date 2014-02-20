*This repository is a mirror of the [component](http://component.io) module [juliangruber/through](http://github.com/juliangruber/through). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/juliangruber-through`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
#through

[![build status](https://secure.travis-ci.org/dominictarr/through.png)](http://travis-ci.org/dominictarr/through)

Easy way to create a `Stream` that is both `readable` and `writable`. Pass in optional `write` and `end` methods. `through` takes care of pause/resume logic.
Use `this.pause()` and `this.resume()` to manage flow.
Check `this.paused` to see current flow state. (write always returns `!this.paused`)

this function is the basis for most of the syncronous streams in [event-stream](http://github.com/dominictarr/event-stream).

``` js
var through = require('through')

through(function write(data) {
    this.emit('data', data)
    //this.pause() 
  },
  function end () { //optional
    this.emit('end')
  })

```

or, with buffering on pause, use `this.queue(data)`,
data *cannot* be `null`. `this.queue(null)` will emit 'end'
when it gets to the `null` element.

``` js
var through = require('through')

through(function write(data) {
    this.queue(data)
    //this.pause() 
  },
  function end () { //optional
    this.queue(null)
  })

```


## License

MIT / Apache2
