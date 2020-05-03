### FileChecker

Class values

- what file to manage
- has there been a change? (boolean)

Functions

- something for threading

  - from https://stackoverflow.com/questions/3393612/run-certain-code-every-n-seconds

    ```python
    import threading
    
    def printit():
      threading.Timer(5.0, printit).start()
      print "Hello, World!"
    
    printit()
    
    # continue with the rest of your code
    ```

    OK, fixed, note that you may also want to set the thread made by `Timer` as a `daemon` in case you want to interrupt the program cleanly by just finishing the main thread -- in that case you'd better set `t = threading.Timer` &c, then `t.daemon = True`, and only then `t.start()` right before the `print "Hello, World!"`

- something for checking that a file has changed

  - getting a file md5 and then getting another md5 and comparing

  - checking the Date Modified field in file metadata

    - use ` stat.ST_MTIME` from the `os` module

  - bonus points i guess is to implement both and have a way to choose between them

    