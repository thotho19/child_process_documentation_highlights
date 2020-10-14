# child_process_documentation_highlights
**What is a child_process mean?**<br>
The **child_process** module provides four different methods for executing external applications:<br>
_**All methods are asynchronous. The right method will depend on what you need.**_
![Screenshot 2020-10-14 004109](https://user-images.githubusercontent.com/42491711/95919292-02f8c980-0db6-11eb-819d-f521f7333e58.png)
- **execFile** : Execute an external application, given a set of arguments, and callback with the buffered output after the process exits.
- **spawn** :  Execute an external application, given a set of arguments, and provide a streaming interface for I/O and events for when the process exits.
- **exec** : Execute one or more commands inside a shell and callback with the buffered output after the process exits.
- **fork** : Execute a Node module as a separate process, given a set of arguments, provide a streaming and evented interface like spawn, and also set up an interprocess communication (**IPC**) channel between the parent and child process.<br>
_**Synchronous Methods**_
- **execFileSync** , **execSync** ,  **spawnSync** : It's same as normal methods but the **Synchronous Methods** will not return until the child process has fully closed. _When a timeout has been encountered and **killSignal** is sent, the method won't return until the process has completely exited._
# 1- child_process.spawn()
- **child_process.spawn schema** :<br>
child_process.spawn(command , [args] , [options]) 
1. **command** : String command that the task needed to ran the process. for example "C:/ffmpeg/bin/ffmpeg.exe"
2. **[args]** : List of string of arguments that the command will execuite it . for example 
```javascript
const args = [
    '-y',
    '-i', 'http://localhost/live/thotho/index.m3u8',
    '-ss', '00:00:01',
    '-vframes', '1',
    '-vf', 'scale=-2:300',
    'C:/ffmpeg/bin/server/thumbnails/thotho.png'
];
```

3. **[options]** : options an Objects <br>

**Options** | **Type** | **Benifts**
------------ | -------------| -------------
**cwd** | String | Current working directory of the child process.
**env** | Object | Environment key-value pairs. Default: process.env.
**argv0** | String | Explicitly set the value of argv[0] sent to the child process. This will be set to command if not specified.
**stdio** | Array or String | Child's stdio configuration. [see options.stdio](https://nodejs.org/api/child_process.html#child_process_options_stdio)
**detached** | Boolean | Prepare child to run independently of its parent process. Specific behavior depends on the platform. [see options.detached](https://nodejs.org/api/child_process.html#child_process_options_detached)
**uid** | Number | Sets the user identity of the process. [see setuid(2)](https://man7.org/linux/man-pages/man2/setuid.2.html)
**gid** | Number | Sets the group identity of the process. [see setgid(2)][https://man7.org/linux/man-pages/man2/setgid.2.html]
**serialization** | String | Specify the kind of serialization used for sending messages between processes. Possible values are 'json' and 'advanced'. See [Advanced serialization](https://nodejs.org/api/child_process.html#child_process_advanced_serialization) for more details. Default: 'json'.
**shell** | String | f true, runs command inside of a shell. Uses _**'/bin/sh' on Unix**_ , and _**process.env.ComSpec on Windows**_ . A different shell can be specified as a string. see [Shell requirements](https://nodejs.org/api/child_process.html#child_process_shell_requirements) and [Default Windows shell](https://nodejs.org/api/child_process.html#child_process_default_windows_shell). **Default**: false (no shell).
**windowsVerbatimArguments** | Boolean | No quoting or escaping of arguments is done on Windows. Ignored on Unix. This is set to true automatically when shell is specified and is CMD. **Default**: false.
**windowsHide** | Boolean | Hide the subprocess console window that would normally be created on Windows systems. **Default**: false.
