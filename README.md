This project is an assembly of various projects. It is meant as fully featured, multi-platform development structure that is easy to use and extend.


### Prerequisites

* Python 2.6 or 2.7
* [cmake 2.8]
    - Only if you want to build documentation or C code
* [A compiler]
    - Only if you want to build C code, compiler itself depends on platform

### Devel Assembly Structure

This paragraph provides you with an overview of the concepts behind the directory structure.
As a rule, no project exists at multiple versions, like its the case in the bdistro assembly.

* src/*
    - Contains source code of various kinds that requires compilation before being useful to the end-user
    - sub-direcotries are named after the project they contain

* etc
    - Various configuration files

* lib/collectives
    - projects maintained by particular interest groups. Code may span various applications and programming languages

* lib/engines/*
    - Each sub-directory contains a project with application specific code, i.e. 'maya' or 'mari'

* lib/core
    - The bcore project, providing basic functionality to all python based projects

* doc/<project>/<version>
    - A repository which contains prebuilt documentation for various projects, supporting multiple versions of each project at the same time

### Top-level Python Package Naming

As python packages will end up in an interpreter namespace which may contain various packages, it is required that top-level packages remain unique through prefixes.

#### Prefixes

Every top level package has at least one prefix.

Prefixes can form hierarchies, making names more specific. Each prefix can only have zero or more children.

* 'b' = byronimo, top-level namespace
* 'a' = application dependent code
* 'c' = mutli-application code and code for particular collectives/workgroups

#### Suffixes

Every top level package has at least one or more suffixes, which may be abbreviated.

Can form a hierarchy, with zero or more children per suffix. Children can be dependent on code from the parent or the parent application.

* application suffixes
    - Take the full name of the application

#### Example

* bamayarv
    - byronimo
    - application
    - maya (name of application)
    - rv (component)

### Projects

Each project lives in its own git repository, and obeys a standard direcotry structure.
Projects are usually named after their top-level python package in case of python projects, but this is by no means a requirement.

* bbuild
    - build system

* bcore
    - general purpose library, stuff to run without additional dependencies
    - Includes Wrapper Engine

* bamaya
    - maya application specific integration layer

* bamayarv
    - 'revised' component for maya application

### Project Assemblies


An assembly is an arrangement of one or more projects. The projects may or may not exist at multiple versions at the same time.

There may be multiple project assemblies, which combine a variety of projects for different purposes.

A prime example for assemblies is the existence of a 'mainline' assembly for developer work, as well as a distribution assembly. Usually they are structurally equal to some extend, even though the distribution assembly might contain transformed projects (e.g. compiled ones), and might miss various projects that are just dependencies needed for compilation of code.

#### Assembly Directory Structure

The directory structure may be absolutely arbitrary, and very much depends on what you want to accomplish.
They should be made to be support consistent data, which implies it to be structured from broad to detailed. Additionally you wouldn't be allowed to store copies of the same dataset in multiple locations of the directory tree.

