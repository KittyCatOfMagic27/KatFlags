# KatFlags
A flag library in C++  
    
This library was written add better flags to the compiler for my language. Its just one header file and fairly minimal. To use it put the file in the ./src of your project and link it to main.cpp with.
```
#include "./flags.h"
```
## Use
To use it, initialize a FlagProxy object with the help description.
```
std::string help_desc = "This is a example help desc!!!\nYou can bring up this page by using the --help flag.";
kf::FlagProxy prox(help_desc);
```
To add a new flag input the flag symbol, function, description of the flag, and the amount arguments it takes.
```
void ECHO_FLAG(std::string word){
  std::cout << word << endl;
}
   
std::string file_flag = "-echo";
std::string file_flag_desc = "Provides ADPL file to compiler (Required).";
prox.AddFlag(file_flag, ECHO_FLAG, file_flag_desc, 1);
```
Note that the function that you input has to output void and take one string as an argument.  
If you have flags that are preprocessed through something else you can add their description like this.
```
prox.AddHelp("--version", "Shows the version of the program.");
```
And to add some text to the end of the help description, do the same but with only one argument.
```
prox.AddHelp("For additional info check README.md and INFO.txt.");
```
Finally to process the command line, use the parse method.
```
prox.Parse(argc, argv);
```
