# filelog

A simple logging backend for [log](//github.com/carpentry-org/log) that works
like [simplelog](//github.com/carpentry-org/simplelog) except it writes its
output to a file of the user’s choosing.

## Example

```clojure
(load "git@github.com:carpentry-org/filelog@0.0.4")

(defn main []
  (do
    (FileLog.install "log.txt" Log.DEBUG)
    (Log.trace "hi") ; will not be written to the file
    (Log.debug "hi again") ; will be written to the file
    (Log.warn "oops") ; will also be written to the file
  )
)
```

## Caveats

Errors opening or writing to the file are silently dropped—the log entry is
simply discarded. A logger should never crash the program it serves, so if you
need guaranteed delivery (e.g. for auditing), consider verifying that the log
path is writable at startup.

<hr/>

Have fun!
