Logger
======

This is a debugging + sentry service for AngularJs apps in both development and production environments. It has four levels of output:

- debug
- info
- warn
- error

It takes a string argument as well as an optional object to output. Usage looks as follows (Coffeescript):

<pre>
Logger.debug 'Initializing app...'
setTimeout ->
    Logger.warn 'App still intializing...
    setTimeout ->
        Logger.info 'App initialized.',
        setTimeout ->
            Logger.error 'Ah! An error.'
                foo: bar # optional object
                bar: baz
        , 1000
    , 1000
, 1000
</pre>

The service can also notify a backend sentry to events. There `config` variable holds configuration as to what should be outputted and which events should trigger $http requests to the server. Configuration might look like this:

<pre>
config =
    mode: 'production'
    sentry: '/api/sentry'
    output: [ 'info', 'error' ]
    notify: [ 'error', 'global' ]
</pre>

The `global` value represents uncaught exceptions. Instead of having to take out all the logs throughout controllers and services, simply change the configuration to what you want outputted and which notifications you want to receive. Output to the console is colored and looks like this:

![alt tag](https://raw.github.com/ishmaelthedestroyer/logger/Logger-2.png)

##Notes
Developed by <a href='http://twitter.com/ishmaelsalive'>Ishmael</a>. <br />

Feedback, suggestions? Tweet me <a href='http://twitter.com/ishmaelsalive'>@IshmaelsAlive</a>. <br />
Need some personal help? Email me @ <a href='mailto:ishmaelthedestroyer@gmail.com?Subject=LazyAngular'>ishmaelthedestroyer@gmail.com</a>