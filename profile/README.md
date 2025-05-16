# Robust Rail NL
An open-source platform for robust train scheduling. Includes a solver, evaluation tool, and instance generator to support research and development in railway operations.



## Important - Build Project
To ease the development it is advised to run the tools in Docker. To facilitate the build process, [.devcontainers](https://github.com/Robust-Rail-NL/.devcontainer) contains the Dockerfile and a configuration for Dev Containers - VS Code. With the help of this repository, all other repositories can be opened in a Docker container, and via Dev Containers development is easier (all repositories are mounted on the Docker), since Dev Containers allow code modification of code in real time.


### Create project folder:

```bash
mkdir Robust-Rail-NL
cd Robust-Rail-NL
```


### Cloning
All the repositories of the project has to be cloned before running Docker.
Note that the cloning process assumes that the git user uses *ssh* key for the authentication to github. 

Navigate to the project folder or create one if it does not exist yet.

```bash
#In the project folder
git clone git@github.com:Robust-Rail-NL/.devcontainer.git
git clone git@github.com:Robust-Rail-NL/robust-rail-generator.git
git clone git@github.com:Robust-Rail-NL/robust-rail-solver.git
git clone git@github.com:Robust-Rail-NL/robust-rail-evaluator.git
git clone git@github.com:Robust-Rail-NL/scenario-planning-inputs.git
```
If **Dev-Container is already installed**: 
* Open the project folder in VS Code.
* `Ctrl+Shif+P` → Dev Containers: Rebuild Container (it can take a few minutes) - this command will use the [Dockerfile](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/Dockerfile) and [devcontainer.json](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/devcontainer.json) definitions under [.devcontainer](https://github.com/Robust-Rail-NL/.devcontainer).


## Build process of robust-rail-tools: 
* [robust-rail-evaluator](https://github.com/Robust-Rail-NL/robust-rail-evaluator)
* [robust-rail-solver](https://github.com/Robust-Rail-NL/robust-rail-solver)
* [robust-rail-generator](https://github.com/Robust-Rail-NL/robust-rail-generator)


## Dev-Container setup (if not installed yet) - and Open Project in VS Docker environment 
The usage of **[Dev-Container](https://code.visualstudio.com/docs/devcontainers/tutorial)** is highly recommended in macOS environment. Running **VS Code** inside a Docker container is useful, since it allows compiling and running tools without platform dependencies. In addition, **Dev-Container** allows to an easy to use dockerized development since the code base can be modified real-time in a docker environment via **VS Code**.

* 1st - Install **Docker**

* 2nd - Install **VS Code** with the **Dev-Container** extension. 

* 3rd - Open the project in **VS Code**

* 4th - `Ctrl+Shif+P` → Dev Containers: Rebuild Container (it can take a few minutes) - this command will use the [Dockerfile](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/Dockerfile) and [devcontainer.json](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/devcontainer.json) definitions unde [.devcontainer](https://github.com/Robust-Rail-NL/.devcontainer).

Note: all the dependencies are already contained by the Docker instance. 

**Building the Dockerfile might take a few minutes (~10 minutes)**.

Next step is the building and usage of the tools. The description of the building and usage of tools are at:
* [robust-rail-evaluator](https://github.com/Robust-Rail-NL/robust-rail-evaluator)
* [robust-rail-solver](https://github.com/Robust-Rail-NL/robust-rail-solver)
* [robust-rail-generator](https://github.com/Robust-Rail-NL/robust-rail-generator)

## Speed up Docker build - (Linux only)
Linux users can speed up the build process. Open [Dockerfile](./Dockerfile): modify `FROM --platform=linux/amd64 ubuntu:20.04` to `FROM ubuntu:20.04`. 
The `--platform=linux/amd64` has been added because new macOS versions did not support the installation of .NET-8 tools, without this specific flag. 


## How to Use ? 

All tools can be used separately. However, a typical process would be as follows:

1) Generate a scenario with [**robust-rail-generator**](https://github.com/Robust-Rail-NL/robust-rail-generator)
    * *Input*:
        * Location file
        * Configuration for custom scenario, or random scenario generation

    * *Output*:
        * Scenario file compatible with **robust-rail-solver**
        * Location file compatible with **robust-rail-solver**
        * Scenario file compatible with **robust-rail-evaluator**

2) Test the correctness of the scenario and location files with the **robust-rail-evaluator** - [CompatibilityTest.cpp](https://github.com/Robust-Rail-NL/robust-rail-evaluator/blob/main/cTORSTest/CompatibilityTest.cpp)
    *  *Input*: 
        * Location, Scenario, Plan (provide empty-path)

    * *Output*:
        * Tells if the Location is correct and the Scenario does not show absurd errors related to first actions

3) Create a schedule plan with the [**robust-rail-solver**](https://github.com/Robust-Rail-NL/robust-rail-solver)
    * *Input*:
        * Scenario and Location file compatible with **robust-rail-solver**
    * *Output*:
        * Plan file (scheduled plan with all the actions)

4) Evaluate plan with [**robust-rail-evaluator**](https://github.com/Robust-Rail-NL/robust-rail-evaluator)
     *  *Input*: 
        * Location, Scenario, Plan

    * *Output*:
        * Tells if the Plan is valid

### Valid scenario, location and plan data 
The repository [**scenario-planning-inputs**](https://github.com/Robust-Rail-NL/scenario-planning-inputs) contains the scenario, location inputs (json files)
that were generated by `robust-rail-generator` component, solved by `robust-rail-solver` component resulting in plans, and finally plans evaluated by `robust-rail-evaluator`.

