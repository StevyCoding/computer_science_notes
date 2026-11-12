Core Java provides complete control over multithreaded programs. You can develop a multithreaded program which can be suspended, resumed, or stopped completely based on your requirements. There are various static methods which you can use on thread objects to control their behavior.

## Methods for Controlling Java Thread

The following table lists the methods for controlling a thread in Java:

| Sr.No. | Method & Description                                                                                                                                                   |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | **`public void suspend()`** <br><br> This method puts a thread in the suspended state and can be resumed using the `resume()` method.                                            |
| 2      | **`public void stop()`** <br><br> This method stops a thread completely.                                                                                                   |
| 3      | **`public void resume()`** <br><br> This method resumes a thread, which was suspended using the `suspend()` method.                                                              |
| 4      | **`public void wait()`** <br><br> Causes the current thread to wait until another thread invokes the `notify()` method.                                                           |
| 5      | **`public void notify()`** <br><br> Wakes up a single thread that is waiting on this object's monitor. ⏰