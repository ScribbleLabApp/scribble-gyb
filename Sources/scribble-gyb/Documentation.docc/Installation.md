# Installation

A comprehensive guide to integrating Scribble GYB into your project for seamless boilerplate code generation.

## Overview

Scribble GYB can be integrated into your project using two primary methods: **(a)** *as a Git submodule* or **(b)** by *manually copying the necessary files* into your project directory. Choose the option that best fits your development workflow.

@TabNavigator {
    @Tab("Git Submodule") {
        To use Scribble GYB, add it to your project either as a Git submodule or by manually copying the files into your project directory. For the Git submodule option, navigate to your project and run the following commands:
        
        ```bash
        git clone https://github.com/ScribbleLabApp/scribble-gyb.git
        git submodule init
        git submodule update
        ```
    }
    
    @Tab("Copying Source Files") {
        For manual integration, clone the repository and copy the contents into a designated directory within your project:
        
        ```bash
        git clone https://github.com/ScribbleLabApp/scribble-gyb.git
        mkdir -p /path/to/your-project/utils
        cp -R scribble-gyb/* /path/to/your-project/utils/
        ```
    }
}
