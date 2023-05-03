Download Link: https://assignmentchef.com/product/solved-cs180-assignment1-usage-of-virtual-machine
<br>
<h1>1           Usage of Virtual Machine</h1>

This course will be using virtual machines (VM). You can write, compile, and run your codes in the virtual machine. By mounting the provided Virtual Hard Disk File, everyone is guaranteed to have an identical and sufficient coding environment. You do not need to set it up on your own.

1.1         Installation

We use Oracle VM VirtualBox in this course. You can download it using the following link: • Windows: https://download.virtualbox.org/virtualbox/6.1.16/VirtualBox-6.1.16-140961-Win.exe • Mac OS:

https://download.virtualbox.org/virtualbox/6.1.16/VirtualBox-6.1.16-140961-OSX.dmg

<ul>

 <li>Linux: You can find the right version corresponding to your own kernel at https://www.virtualbox.org/wiki/Linux_Downloads.</li>

</ul>

<h2>1.2         Download the Virtual Hard Disk File (.vdi)</h2>

We have packed all the software you need and developing environment into one single vdi file:

https://ucsb.box.com/s/gyhsyc4q7b6se9wof03740qratbgjakm. You can download and unzip it. The unzipped file (Ubuntu 18.04.2 (64bit).vdi) can be loaded by Virtual Box directly (see next subsection).

<h2>1.3         Virtual Box Configuration</h2>

Open Virtual Box, click <strong>New</strong>. Fill in the blanks using the following information:

<ul>

 <li>Name: whatever you want;</li>

 <li>Machine Folder: use default settings or whatever you want;</li>

 <li>Type: Linux;</li>

 <li>Version: Ubuntu (64-bit).</li>

</ul>

Then click <strong>Continue</strong>. On the next page, we recommend you to set the memory size to no less than 2GB.

In the <strong>Hard disk </strong>page, choose <strong>Use an existing virtual hard disk file</strong>, and select the vdi file you just downloaded. Click <strong>Create</strong>, and you are done.

The password of the given system is <strong>Ilovegraphics</strong>.

<h2>1.4         Install Guest Additions</h2>

After you enter the system, please install guest additions, by clicking <strong>Devices </strong>→ <strong>Insert Guest Additions CD image…</strong>.

If this method doesn’t work for you, you can also try to install using command line: open terminal (Ctrl-Alt-t), then execute the following commands:

<ul>

 <li>sudo mkdir -p /media/cdrom</li>

 <li>sudo mount -t auto /dev/cdrom /media/cdrom/</li>

 <li>cd /media/cdrom/</li>

 <li>sudo sh VBoxLinuxAdditions.run</li>

</ul>

After doing so, restart VM to finish the installation.

<h2>1.5         Import codes</h2>

There are many ways to do so. Here is one example: you can directly drag your files from your host operating system into the VM. Make sure the <strong>Drag and Drop </strong>feature is set to <strong>Bidirectional</strong>:

When the code skeleton is imported into the VM, you can view and edit it using Visual Studio Code (VS Code). This should be the default editor of cpp files.

<h2>1.6         VM Performance Settings</h2>

To improve the performance of the VM, power off the VM and then select go to <strong>Settings </strong>(the Gear Icon) in the VirtualBox Manager.

Then in the settings window go to <strong>System </strong>tab then go to <strong>Motherboard </strong>Tab. Increase the base memory to any desired value but be sure not to set it in the red region.

After changing the available memory, increase the available cores by going to the <strong>Processor </strong>tab. Set the Processor to any desired value but again be sure not to set any value in the red region.

<h1>2           Code Skeleton</h1>

The code skeleton is provided in the sample code main.cpp.

<h2>2.1         Developing Tools</h2>

We recommend you to use Visual Studio Code (VS Code) as the editor and compile and run your codes in the terminal.

After you drag the code into your VM, open VS Code, select <strong>File </strong>→ <strong>Open Folder </strong>to open the folder containing the code.

<h2>2.2         C++ 101</h2>

This subsection provides some basic knowledge about C++ that is relevant to the course assignments. If you want to learn more, please go to https://devdocs.io/cpp/ or Stack Overflow.

<h3>2.2.1         Headers</h3>

C++ adopts the convention of using header files to contain declarations. You make the declarations in a header file, then use the #include directive in every cpp file or other header files that require that declaration. The #include directive inserts a copy of the header file directly into the cpp file before compilation.

In practice, you can include additional libraries by using #include:

<ul>

 <li>#include &lt;cmath&gt;</li>

 <li>#include &lt;iostream&gt;</li>

</ul>

The above codes include the necessary libraries for C++ input/output and mathematical calculations.

<h3>2.2.2         Functions</h3>

A function is a block of code that only runs when it is called. The function named with <strong>main </strong>is the entry point of a program.

<ul>

 <li>int main() {</li>

 <li>float a = 1.0, b = 2.0;</li>

 <li>std::cout &lt;&lt; a &lt;&lt; std::endl;</li>

 <li>std::cout &lt;&lt; a/b &lt;&lt; std::endl;</li>

 <li>std::cout &lt;&lt; std::sqrt(a) &lt;&lt; std::endl;</li>

 <li>std::cout &lt;&lt; std::acos(-1) &lt;&lt; std::endl;</li>

 <li>std::cout &lt;&lt; std::sin(30.0/180.0*acos(-1)) &lt;&lt; std::endl;</li>

 <li>return 0;</li>

 <li>}</li>

</ul>

The above program outputs the following calculation results: <em>a</em>, <em><u><sup>a</sup></u><sub>b</sub></em>, <em>a</em>, arccos(−1), sin(30<sup>◦</sup>), where <em>a </em>= 1 and <em>b </em>= 2, and exits safely.

<h3>2.2.3         Common Errors</h3>

<ul>

 <li>Compile Error: try to solve it based on the error message. If you cannot solve it by yourself, you can search the error message on Stack Overflow to find similar cases.</li>

 <li>undefined reference to xxx: usually linking errors. Check if the function is declared in the header file, but has not been implemented in the cpp Or check the linking configurations in CMakeLists.txt.</li>

 <li>Segmentation Fault: usually caused by index out of bounds, too much stack usage.</li>

 <li>Bus Error: the causes are usually similar to the causes of the segmentation fault.</li>

 <li>Math Error: usually caused by dividing it by 0.</li>

</ul>

<h2>2.3         Eigen</h2>

This course uses Eigen as the C++ library for linear algebra. Its official documentation can be found at http://eigen.tuxfamily.org.

<h3>2.3.1         Headers</h3>

In order to use Eigen in your project, it needs to be included:

1 #include &lt;eigen3/Eigen/Core&gt;

<h3>2.3.2         Vectors and Matrices</h3>

This part only provides an overview of vectors and matrices operations in Eigen. For a more thorough explanation, please refer to https://eigen.tuxfamily.org/dox/group__TutorialMatrixArithmetic. html.

<ul>

 <li>// Example of vectors</li>

 <li>std::cout &lt;&lt; “Example of vectors 
”;</li>

 <li>// vectors definition</li>

 <li>Eigen::Vector3f v(1.0f,2.0f,3.0f);</li>

 <li>Eigen::Vector3f w(1.0f,0.0f,0.0f);</li>

 <li>// vectors output</li>

 <li>std::cout &lt;&lt; “Example of output 
”;</li>

 <li>std::cout &lt;&lt; v &lt;&lt; std::endl;</li>

 <li>// vectors addition</li>

 <li>std::cout &lt;&lt; “Example of addition 
”;</li>

 <li>std::cout &lt;&lt; v + w &lt;&lt; std::endl; 12 // vectors scalar multiplication</li>

 <li>std::cout &lt;&lt; “Example of scalar multiplication 
”;</li>

 <li>std::cout &lt;&lt; v * 3.0f &lt;&lt; std::endl;</li>

 <li>std::cout &lt;&lt; 2.0f * v &lt;&lt; std::endl;</li>

</ul>

The above code shows the definition, output, addition, and scalar multiplication of 3D floating-point vectors. Please try computing the dot product of two vectors on your own.

<ul>

 <li>// Example of matrices</li>

 <li>std::cout &lt;&lt; “Example of matrices 
”;</li>

 <li>// matrices definition</li>

 <li>Eigen::Matrix3f i,j;</li>

 <li>i &lt;&lt; 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0;</li>

 <li>j &lt;&lt; 2.0, 3.0, 1.0, 4.0, 6.0, 5.0, 9.0, 7.0, 8.0;</li>

 <li>// matrices output</li>

 <li>std::cout &lt;&lt; “Example of output 
”;</li>

 <li>std::cout &lt;&lt; i &lt;&lt; std::endl;</li>

 <li>// matrices addition i + j</li>

 <li>// matrices scalar multiplication i * 2.0</li>

 <li>// matrices multiplication i * j</li>

 <li>// multiply a matrix and a vector i * v</li>

</ul>

This sample provides the definition and output of matrices. Please explore the usage described in the comments above.

<h2>2.4         Code Compilation and Execution</h2>

This course recommends you to use <strong>cmake </strong>to build your program. After finishing writing codes, go to the current folder in the terminal window, then run the following commands to compile and run your program:

<ul>

 <li># Make a folder named build, and enter it. This is the folder that stores all the compiling and linking results.</li>

 <li>mkdir build; cd build</li>

</ul>

3

<ul>

 <li># .. means the parent directory. It’s the directory containing CMakeLists.txt. This step generates a Makefile using cmake.</li>

 <li>cmake ..</li>

</ul>

6

<ul>

 <li># Compile your program. ‘Make’ will read the Makefile by default. Errors will show up in the terminal if there is something wrong.</li>

 <li>make</li>

</ul>

9

<ul>

 <li># Run your program. ‘assignment1’ is the name of the executable file. You can change it in the CMakeLists.txt.</li>

 <li>./assignment1</li>

</ul>

12

<ul>

 <li># Delete all the compiled results before submission.</li>

 <li>cd ..</li>

 <li>rm -r build</li>

</ul>

<h1>3           Problem Set</h1>

For problems 2, 3 and 4 go to main.cpp provided with the assignment. Add codes in appropriate places.

<table width="626">

 <tbody>

  <tr>

   <td width="577">01. (5 points) Describe what this 2D homogeneous transform matrix does for a point: <sub></sub>1 0</td>

   <td width="32">−100</td>

   <td width="17"></td>

  </tr>

 </tbody>

</table>

<ol start="2">

 <li>(5 points) Write the 3 × 3 transformation matrix for a 45<sup>◦ </sup><strong>clockwise </strong>rotation in 2D (assuming homogeneous coordinates). Populate the rot_45 matrix variable using &lt;&lt; operator in cpp.</li>

 <li>(5 points) Write the 4 × 4 transform matrix to move a point by (3<em>,</em>4<em>,</em>5). Populate the translation matrix variable using &lt;&lt; operator in cpp.</li>

 <li>(20 points) In computer graphics, we often need to map points in one rectangle to a new rectangle area. Suppose the bottom left corner and top right corner of original rectangle are (2<em>,</em>3) and (4<em>,</em>5). The bottom left corner and top right corner of new rectangle are (3<em>,</em>2) and (5<em>,</em>4). This can be achieved by a sequence of three steps:

  <ul>

   <li>Move point (2<em>,</em>3) to the origin.</li>

   <li>Scale the rectangle to be the same size as the target rectangle.</li>

   <li>Move back points to new position.</li>

  </ul></li>

</ol>

Populate the matrix for each step, and the multiplication result of these matrices in the correct order in main.cpp.