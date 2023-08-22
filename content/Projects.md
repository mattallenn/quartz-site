# cspeed
### A simple, lightweight, fast typing speed game written in C.

## Installation

1. Make sure you have the [Dependencies](#dependencies)
2. Run `git clone https://github/mattallenn/cspeed.git`
3. Compile `cspeed.c`, if you have gcc installed, run `make`
4. Run `./cspeed`

## Dependencies
**ncurses** - terminal manipulation  
- macOS `brew install ncurses`
- Linux
	- Arch: `sudo pacman -S ncurses`
 	- Ubuntu: `sudo apt-get install libncurses5-dev libncursesw5-dev`
  	- *For other distros / package managers, feel free submit a pull request of the command needed*
- Windows `god help you, try this link though https://e-l.unifi.it/pluginfile.php/805205/mod_resource/content/0/ncurses%20installation%20-%20en.pdf`

## Tutorial (**INCOMPLETE**)


**1. Open File**
- Check for file errors 
	``` c
	if (file == NULL) {
        printf("Cannot open file\n");
        exit(1); 
    }
	```

**2. Load file contents into an array**
- define the number of lines and max number of chars in each line  
- Initialize 2d array `char lines[LINE_NUM][STR]` where `LINE_NUM` is the line that the word is on (its index), and `CHARS` is the array of chars that make up that word. 
- use `fgets()` to load contents from file one line at a time eg. `fgets(string, max num of chars, file)`
- store str into its own index using a line counter eg.
	```c
    #include <string.h>

    //Reads file, adding each word to a 2d array
    while (fgets(lines[line_counter], 12, file) != NULL) {

        //Removes newline character from each word
        lines[line_counter][strlen(lines[line_counter]) - 1] = '\0';

        //printf("%s", lines[line_counter]);

        line_counter++;

        if (line_counter >= 1000) {
            break;
        }
    }
	```

**3. Generate random words**  
- Include `<time.h` for the `srand()` function
- Use the time since epoch to generate a seed 
- Iterate through array and pick random words
	```c    

    #include <time.h>
  
    //prints random word from array
    srand(time(NULL));
    
    for (int i = 0; i < 1000; i++) {
        int random = rand() % 1000;
        printf("%s ", lines[random]);
    }

	```

