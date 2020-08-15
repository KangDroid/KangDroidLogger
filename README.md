The Logger Library
===================

Intro
------
Acually, this log library was buil / developed for personal purpose[i.e personal projects], but I think its better to share it.<br><br>
It is just a simple library with file-write support!

To use[Overall]
------
This lib has two main log function, such as LOG_E and LOG_V. As you can see those name, they stands for "Log Error", "Log Verbose".[I am thinking of supporting Warning/Fatal, but not yet.] <br>
As you can see my header file, there are two Log Error and Log Verbose function. We can use all of them ofcourse, but there are little-bit-different between functions.

To use[log_e | Static function]
-------------------------------
What it does: Write Error Log<br>
Parameter:
|param_name|type|desc.|
|----------|----|-----|
|line|Integer[int]|Actual line of code|
|fcode|String[string]|Actual name of function|
|output|String[string]|Actual log contents|
|is_command|Boolean[bool]|Whether to include \n or not|

Example usage: ``Logger::log_e(10, "testFunction", "ERROR OCCURED" false);``<br>
Example output: ``2020-08-05.22:32:13::[E]/testFunction:10: ERROR OCCRED``

To use[LOG_E | Macro Function]
-------------------------------
What it does: Mostly same as log_e, but automates line/fcode parameter, is_command, only you need to put is log its contents[output]<br>
Parameter:
|param_name|type|desc.|
|----------|----|-----|
|output|String[string]|Actual log contents|

Assuming executing LOG_E on ``2020-08-05.22:32:13``, and function name is ``testFunction``.<br>
Example usage: ``LOG_E("ERROR OCCURED");``<br>
Example output: ``2020-08-05.22:32:13::[E]/testFunction:10: ERROR OCCRED``<br><br>
The C++ Macro, ``"__LINE__"``, ``"__func__"`` will automatically swap log_e's function parameter: line and fcode.

To use[log_v | Static function]
-------------------------------
What it does: Write Verbose Log<br>
Parameter:
|param_name|type|desc.|
|----------|----|-----|
|line|Integer[int]|Actual line of code|
|fcode|String[string]|Actual name of function|
|output|String[string]|Actual log contents|
|is_command|Boolean[bool]|Whether to include \n or not|

Example usage: ``Logger::log_v(10, "testFunction", "Done something" false);``<br>
Example output: ``2020-08-05.22:32:13::[V]/testFunction:10: Done something``

To use[LOG_V| Macro Function]
-------------------------------
What it does: Mostly same as log_v, but automates line/fcode parameter, is_command, only you need to put is log its contents[output]<br>
Parameter:
|param_name|type|desc.|
|----------|----|-----|
|output|String[string]|Actual log contents|

Assuming executing LOG_E on ``2020-08-05.22:32:13``, and function name is ``testFunction``.<br>
Example usage: ``LOG_V("Done Something");``<br>
Example output: ``2020-08-05.22:32:13::[V]/testFunction:10: Done Something``<br><br>
The C++ Macro, ``"__LINE__"``, ``"__func__"`` will automatically swap log_e's function parameter: line and fcode.

To Use[initiate_stream | static bool function]
----------------------------------------------
What it does: Initiate Log Stream[File]<br>
Parameter:
|param_name|type|desc.|
|----------|----|-----|
|path|String[string]|Path to save log with file name|

Example usage: ``Logger::initiate_stream("/home/kangdroid/test.log");``<br>
Example output: true if stream succesfully created file, false otherwise.


To Use[close_stream | static bool function]
----------------------------------------------
What it does: Close Log Stream[File]<br>
Parameter: [Nope]

Example usage: ``Logger::close_stream();``<br>
Example output: true if stream succesfully closed file, false otherwise.


Example Use[Overall]
--------------------
```
#include <iostream>
#include "Logger.h"

using namespace std;

int main(void) {
    if (Logger::initiate_stream("/home/kangdroid/Desktop/log_test.log")) {
        LOG_V("Just successfully initiated stream!");
    } else {
        LOG_E("Somehow, it failed to initiate stream[File], Check permission!");
    }
    Logger::close_stream();
    return 0;
}
```