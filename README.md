<img src="./cover.png"></img>

### Use Julia for Deep Learning with ease
This project contains the basics of the programming language [Julia](https://julialang.org/) in general and for Machine Learning and Deep Learning.


- [Reasons to use Julia for Deep learning](#reasons-to-use-julia-for-deep-learning)
- [Installation](#installation)
- [REPL](#repl)
- [Interactive Julia Notebooks](#interactive-julia-notebooks)
- [Package and Environment Management](#package-and-environment-management)
- [Basic Syntax](#basic-syntax)

<br><br>

---
### Reasons to use Julia for Deep learning

While python was and still is the main language for many task, also for deep learning, using Julia can be very rewarding. Julia is build for data science, machine learning and depp learning. It provides:
- GPU support
- parallel computing on CPU or GPU
- libraries for data processing, visualisation, machine learningand deep neuronal networks
- high speed runtime (due to compilation)
- packaging system with easy to use environment management 
- easy syntax
- and more

<br><br>

---
### Installation

1. Download Julia from [the official website](https://julialang.org/downloads/)
2. Under **Windows** just run the exe and follow the steps. Under **Linux** extract the downloaded file and add to the system variables PATH with: 
    ```terminal
    sudo tar -xvzf julia-\*.tar.gz -C /opt/ 
    export PATH="$PATH:/opt/julia/bin"
    ```
3. Start Julia by typing "**julia**" in the terminal/bash. This will start the [REPL](#repl). Else you can open an IDE, like Visual Studio Code (using the Julia extension) or writing your code in plain text editors and running them from terminal with **julia your_file.jl**. Another way is to start a Jupyter Server and writting julia code in a ipynb file. Here you also can use Visual Studio Code or the [core Jupyter](https://jupyter.org/install) or [here](https://github.com/jupyterlab/jupyterlab-desktop) or [with IJulia](#interactive-julia-notebooks).

<br>

Installation of Env used here:
1. Open Julia REPL
2. Navigate to this project
    ```julia
    cd("F:/src/HelpJl")
    pwd()
    using Pkg
    Pkg.activate(".")
    Pkg.add(["DataFrames", "IJulia", "Flux", "MLJ", "CUDA", "cuDNN"])
    Pkg.update()
    Pkg.status()
    ```
    Alternativly you can use the already existing files if you use this project:
    ```julia
    cd("F:/src/HelpJl")
    pwd()
    using Pkg
    Pkg.activate(".")
    Pkg.instantiate()
    Pkg.status()
    ```

<br><br>

---
### REPL

The REPL (Read-Eval-Prit Loop) is a lightweight Julia console. There you run Julia commands line by line. It is perfect for installing packages, organize virtual environments and experiment/test.

<br>

To start the REPL, just open a terminal and type **julia**.

<br>

Importing packages:
```terminal
using DataFrames
df = DataFrame(A=1:7, B=rand(7))
println(df)
```

<br>

Using **Package Mode** by pressing **]**.

<br>

Using **help mode** to print information about code like functions and classes. Just type **?** for the code:
```terminal
?println
```

<br>

Using **shell mode** to run an system call by using **;** before the statement.
```terminal
;ls
```

> I do not recommend using the shell mode (at least under windows). Instead I recommend using the given os functions directly in julia → [see this notebook](./src/os.ipynb).

<br>

For profiling you also can use @time and @benchmark before the running code with one whitespace as seperator.
```terminal
@time sum(1:10000)
```

<br><br>

---
### Interactive Julia Notebooks

Interactive Julia notebooks are coding file-format, where you code in multiple blocks. Every block can be runned sololy and there are also markdown blocks, for nice commenting and structuring.

For using interactive Julia notebooks, first you have to install interactive Julia librarie: you have to open your terminal and type:
```terminal
julia
]
add IJulia
```

> Hint: The jupyter notebook software can alternativly also be installed with python: pip install jupyter

Now you can use the .ipynb files to write interactive Julia code and also can use Markdown blocks to show and explain your code better.

You can open the juypter notebook by typing following in the terminal:

```terminal
julia
using IJulia
notebook()
```

> Hint: You can use @time and @benchmark to profile and debug blocks/cells in your notebooks.

<br><br>

---
### Package and Environment Management

Julia have comes with it's own packaging system called **Pkg.jl**. To open it, open the terminal, type "julia" and then type "**]**" (and press enter).<br>Now you can install a package. For example if you want to install the Flux.jl package for deep learning tasks:
```terminal
add Flux
```

<br>

Multiple packages:
```terminal
add Flux MLJ CUDA DataFrames
```

<br>

Specific Version:
```terminal
add Flux@0.12.5
```

<br>

You can remove packages with:
```terminal
rm Flux
```

<br>

Updating your packages automatically:
```terminal
update
```

<br>

Show installed packages:
```terminal
status
```

<br><br>

Next we have the **management** of different **environments**. For different projects you need different packages with maybe different versions. In Julia it is easy to activate and create an virtual environment. Open the terminal, navigate to your project folder, type julia and press ], then type:
```terminal
activate .
```

You can use the REPL to navigate to your target folder, I recommend using the julia mode not the shell mode via:
```julia
pwd()          # Show current directory
readdir()      # List Files and Folders
cd("C:/Users/YourName/Projects")   # Change your current directory
# or
cd(raw"C:\Users\YourName\Projects")
``` 

<br>

A virtual environment is defined by the project.toml and the Manifest.toml.<br>Every package you install after the activate command will be added only at the virtual environment.

<br><br>

It is also possible to open the terminal, type julia and then importing the Pkg.jl package:
```terminal
using Pkg
Pkg.activate(".")
Pkg.add("Flux")
Pkg.rm("Flux")
Pkg.update()
```

<br><br>

To install/copy an existing environment. Copy the **Project.toml** and **Manifest.toml** files to your new project and then open your terminal and navigate to your new project folder:
```terminal
julia
using Pkg
Pkg.activate(".")
Pkg.instantiate()
```

<br><br>

Checkout your env:
```julia
using Pkg

Base.active_project()
Pkg.status()
Pkg.envdir()
```

<br><br>

---
### Basic Syntax








