# Convenient and customizable solution for monitoring and terminating processes - Windows only

## pip install constant-check-and-kill

#### Tested against Windows 10 / Python 3.10 / Anaconda


The constant_check_and_kill module provides a convenient and customizable solution for monitoring and terminating processes, offering users greater control and automation in managing their system's processes.

It can be useful for system administrators, developers, or users who need to monitor and terminate specific processes based on configurable criteria. Here are some potential use cases and advantages of using this module:



### Flexibility: 

The module provides configurable options such as executable path patterns, regular expression support, and delay between process checks, allowing users to tailor the process monitoring and termination behavior to their specific needs.


### Automation: 

The module allows for continuous monitoring and automatic termination of processes, reducing the need for manual intervention and saving time.

### Customization: 

Users can define their own process termination criteria based on executable path patterns or regular expressions, giving them fine-grained control over which processes to target.

### Scalability: 

The module can handle multiple processes simultaneously, making it suitable for environments with a large number of processes to monitor and terminate.

### Control: 

Users can choose to terminate only the first matching process or continue monitoring and terminating subsequent matches, providing flexibility in managing process termination behavior.


```python
constant_check_and_kill(
    exe_path: str | None = None,
    is_regex: int | bool = 1,
    flags: int = re.I,
    delay: float | int = 1.0,
    close_after_first: int | bool = 0,
):
    r"""
    Continuously checks for running processes and kills them if they match the specified criteria.

    Args:
        exe_path (str | None): The path or regex pattern of the processes to be killed.
        is_regex (int | bool): Flag indicating if `exe_path` is a regex pattern (default: 1).
        flags (int): Additional flags for the regex pattern matching (default: re.I).
        delay (float | int): Delay in seconds between process checks (default: 1.0).
        close_after_first (int | bool): Flag indicating whether to exit after killing the first matching process (default: 0).

    Returns:
        Callable[[], None]: A partial function that can be used to stop the continuous process checking and killing.

    Raises:
        None

    Example usage:

    Killing one process - function call:
    This example demonstrates how to kill a single process by calling the kill_proc function with the desired process ID (PID).
    The process with the specified PID will be terminated.

    kill_proc(pid=21360)
    ############################################################
    Constantly checking if processes exist and kill them - CLI:
    This example shows how to use the script from the command line to continuously monitor and kill processes that match a
    specific executable path pattern. The command should be executed in the following format:
    
    # adjust the path
    python "C:\ProgramData\anaconda3\envs\dfdir\Lib\site-packages\constant_check_and_kill\__init__.py" --exe_path "(?:calculator.exe|chrome.exe)$" --is_regex 1 --flags 2 --delay 0.1 --close_after_first 0
    --exe_path: The regular expression pattern specifying the executable path(s) of the target processes.
    --is_regex: A flag indicating whether the exe_path argument should be treated as a regular expression (1 for True, 0 for False).
    --flags: Additional flags for the regular expression pattern matching.
    --delay: The delay in seconds between each process check.
    --close_after_first: A flag indicating whether to exit the script after killing the first matching process (1 for True, 0 for False).
    ############################################################
    Constantly checking if processes exist and kill them - function call:
    This example demonstrates how to continuously monitor and kill processes that match a specific executable path pattern
    by calling the constant_check_and_kill function directly.
    from constant_check_and_kill import constant_check_and_kill

    constant_check_and_kill(
        exe_path="notepad.exe$",
        is_regex=True,
        flags=re.I,
        delay=1.0,
        close_after_first=False,
    )
    exe_path: The regular expression pattern or exact executable path of the target processes.
    is_regex: A flag indicating whether the exe_path argument should be treated as a regular expression (True) or an exact path (False).
    flags: Additional flags for the regular expression pattern matching.
    delay: The delay in seconds between each process check.
    close_after_first: A flag indicating whether to exit the script after killing the first matching process (True) or
    continue monitoring and killing other matching processes (False).
```
