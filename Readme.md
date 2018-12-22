# Antlr4BuildTasks

This is a modification of Hartwell's [Antlr4cs](https://github.com/tunnelvisionlabs/antlr4cs),
containing the Antlr4 Task wrapper assembly,
the targets and props files for Antlr files with MSBuild,
and a file properties schema for Antlr files with Visual Studio IDE.
The purpose of the package is to integrate the Antlr tool
into the building of NET programs that reference Antlr using the [Java-based
Antlr tool](https://www.antlr.org/download.html). During a build,
it calls the Antlr tool to generate the source code for the parser from grammar,
then compiles and links. Using this package, you don't have to manually
run the Antlr tool outside the IDE, then go back to the IDE to complete the build. It is
all done seamlessly in the IDE. This project also assumes you are compiling for C# NET,
using the Antlr runtime library for NET, [Antlr4.Runtime.Standard](https://www.nuget.org/packages/Antlr4.Runtime.Standard).
The advantage of this package is that it decouples the Java-based Antlr tool from the package
itself, allowing one to work
with any version of Antlr, instead of using Hartwell's 
[Antlr4.CodeGenerate](https://www.nuget.org/packages/Antlr4.CodeGenerator/)
which lags several revisions behind the latest Java-based Antlr tool.

This package predicates that you
* Installed Java tool chain.
* Downloaded the Java-based Antlr tool chain (a jar file).
* Set the environment variable JAVA_HOME to the directory of the java installation.
* Set the environment variable Antlr4BuildTasks to the path of the downloaded Antlr jar file.
* Do not include the generated .cs Antlr parser files in the CSPROJ file for your program. The generated parser code is placed in the build temp output directory and automatically included.

This package is a Net Standard assembly and works on Linux or Windows, and works only for Antlr4 grammars.

To set grammar specific options for the Antlr tool, use VS2017 file properties or set the options in the CSPROJ file.

Language support in Visual Studio 2017 itself--
e.g. colorized tagging of the Antlr grammar, go to definition, reformat, etc.--
is a separate product, not part of the build rules for Antlr grammar files,
which is what this package supports. You can use Hartwell’s [Antlr Language Support](https://marketplace.visualstudio.com/items?itemName=SamHarwell.ANTLRLanguageSupport)
extension, my own [AntlrVSIX](https://marketplace.visualstudio.com/items?itemName=KenDomino.AntlrVSIX) extension, or another.

You can see the NuGet package in action [here on Youtube](https://www.youtube.com/watch?v=Flfequp_Dy4).
The Net Core code for the Antlr Hello World example is [here in Github](https://github.com/kaby76/AntlrHW).
