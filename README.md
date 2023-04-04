# Setting up WSL2 for C/C++/OpenGL Development

This guide provides step-by-step instructions on how to set up Windows Subsystem for Linux (WSL) for C/C++/OpenGL development. By the end of this guide, you should have a fully functional development environment for creating C/C++/OpenGL applications using WSL2 on Windows 10/11.


## Prerequisites

Before you begin, make sure you have the following prerequisites installed on your Windows 10 machine:
- For x64 systems: Version 1903 or later, with Build 18362 or later.
- For ARM64 systems: Version 2004 or later, with Build 19041 or later.

or Windows 11.


## Installing WSL2
Follow the steps below to install WSL2 on your Windows 10/11 machine:

1. Open PowerShell as an administrator.

2. Run the following command to enable the Windows Subsystem for Linux feature:

```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

3. Restart your computer when prompted.

4. Download and install the [WSL2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

5. Open PowerShell as an administrator again.

6. Run the following command to set WSL2 as the default version:

```PowerShell
wsl --set-default-version 2
```


## Installing a Linux Distribution & Windows Subsystem for Linux(Required for GUI)

1. Open the Microsoft Store and search for your preferred Linux distribution (e.g., Ubuntu, Debian, or Kali Linux). Click "Get" to install the distribution on your WSL. We suggest installing [Ubuntu 22.04.2 LTS](https://apps.microsoft.com/store/detail/ubuntu-22042-lts).

2. Now Install [Windows Subsystem for Linux](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux)(WSL) lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dual boot setup.

3. Launch and configure Linux distribution: Open the Start menu and click on the Linux distribution you installed to launch it. Follow the on-screen instructions to set up the Linux distribution.

## Setting up the Development Environment

Install development tools: In the Linux terminal, run the following command to install the necessary development tools:

```shell
sudo apt update && sudo apt install build-essential mesa-utils libgl1-mesa-dev -y
```

This command installs the build-essential package, which includes compilers and other tools for building C/C++ applications, as well as the mesa-utils and libgl1-mesa-dev packages, which are necessary for OpenGL development.


## Setting up IDE

In addition to using the terminal to write and compile code, you can also set up an Integrated Development Environment (IDE) to make the development process smoother. Here are steps to set up two popular IDEs, Visual Studio Code(Windows Native) and Gedit(WSL GUI):

### Visual Studio Code

1. Download and install [Visual Studio Code](https://code.visualstudio.com/).

2. Open Visual Studio Code and install the Remote Development extension. This extension allows you to develop in a remote environment, such as a WSL distribution.

3. Connect Visual Studio Code to WSL2: In Visual Studio Code, click on the Remote Explorer icon on the left-hand side. Click on the "Connect to a remote host" button and select "WSL: Ubuntu" (or the Linux distribution you installed). Visual Studio Code will then connect to your WSL2 instance.

4. Create a new C/C++/OpenGL project: In Visual Studio Code, create a new folder for your project. Open a terminal window in Visual Studio Code (Ctrl + Shift + `) and navigate to your project folder. Use your preferred method to create a new C/C++/OpenGL project (e.g., using a code template or by creating a new file).

5. Build and run your project: Use the terminal in Visual Studio Code to build and run your C/C++/OpenGL project.

### Gedit

1. Install Gedit in WSL: Open the terminal and run the following command:

```shell
sudo apt update && sudo apt install gedit
```

2. Open Gedit: In the terminal, run the following command to open Gedit:

```shell
gedit
```

3. Create a new C/C++/OpenGL project: In Gedit, create a new file for your project. Use your preferred method to create a new C/C++/OpenGL project (e.g., using a code template or by creating a new file).

4. Build and run your project: Use the terminal in WSL to build and run your C/C++/OpenGL project.


## Create and compile
This section will guide you through creating and compiling C, C++, and OpenGL files using the terminal in WSL.

### Example: C file

1. Create a new file with the extension `.c`(ex. hello.c).

2. Write your C code in the file, such as the following "hello world" program:

```c
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    return 0;
}

```

3. Save the file.

4. In the terminal, navigate to the directory where the file is located.

5. Compile the C file using the following command:

```shell
gcc -o hello hello.c
```

6. Run the compiled program using the following command:

```shell
./hello
```

### Example: C++ file

1. Create a new file with the extension `.cpp`(ex. hello.cpp).

2. Write your C++ code in the file, such as the following "hello world" program:

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, world!\n";
    return 0;
}

```

3. Save the file.

4. In the terminal, navigate to the directory where the file is located.

5. Compile the C++ file using the following command:

```shell
g++ -o hello hello.cpp
```

6. Run the compiled program using the following command:

```shell
./hello
```

### Example: OpenGL file(C)

1. Create a new file with the extension `.c`(ex. triangle.c).

2. Write your OpenGL code in the file, such as the following "triangle" program:

```c
#include <GL/gl.h>
#include <GL/glut.h>

void display() {
    glClear(GL_COLOR_BUFFER_BIT);

    glBegin(GL_TRIANGLES);
    glColor3f(1.0, 0.0, 0.0);
    glVertex2f(-0.5, -0.5);
    glColor3f(0.0, 1.0, 0.0);
    glVertex2f(0.5, -0.5);
    glColor3f(0.0, 0.0, 1.0);
    glVertex2f(0.0, 0.5);
    glEnd();

    glFlush();
}

int main(int argc, char** argv) {
    glutInit(&argc, argv);
    glutCreateWindow("OpenGL Test");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}

```

3. Save the file.

4. In the terminal, navigate to the directory where the file is located.

5. Compile the OpenGL file using the following command:

```shell
gcc -o triangle triangle.c -lGL -lglut
```

6. Run the compiled program using the following command:

```shell
./triangle
```





<br>
Congratulations! You now have a fully functional development environment for C/C++/OpenGL development using WSL2 on Windows 10/11, complete with an IDE of your choice.
<hr>
