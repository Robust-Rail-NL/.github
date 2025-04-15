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
```
If **Dev-Container is already installed**: 
* Open the project folder in VS Code.
* `Ctrl+Shif+P` → Dev Containers: Rebuild Container (it can take a few minutes) - this command will use the [Dockerfile](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/Dockerfile) and [devcontainer.json](https://github.com/Robust-Rail-NL/.devcontainer/blob/main/devcontainer.json) definitions under [.devcontainer](https://github.com/Robust-Rail-NL/.devcontainer).



## Dev-Container setup (Installed yet) - and Open Project in VS Docker environment 
The usage of **[Dev-Container](https://code.visualstudio.com/docs/devcontainers/tutorial)** is highly recommended in macOS environment. Running **VS Code** inside a Docker container is useful, since it allows compiling and use cTORS without platform dependencies. In addition, **Dev-Container** allows to an easy to use dockerized development since the mounted `ctors` code base can be modified real-time in a docker environment via **VS Code**.

* 1st - Install **Docker**

* 2nd - Install **VS Code** with the **Dev-Container** extension. 

* 3rd - Open the project in **VS Code**

* 4th - `Ctrl+Shif+P` → Dev Containers: Rebuild Container (it can take a few minutes) - this command will use the [Dockerfile](.devcontainer/Dockerfile) and [devcontainer.json](.devcontainer/devcontainer.json) definitions unde [.devcontainer](.devcontainer).

* 5th - Build process of the 
    * [robust-rail-evaluator](https://github.com/Robust-Rail-NL/robust-rail-evaluator)
    * [robust-rail-solver](https://github.com/Robust-Rail-NL/robust-rail-solver)
    * [robust-rail-generator](https://github.com/Robust-Rail-NL/robust-rail-generator)

Note: all the dependencies are already contained by the Docker instance. 

**Building the Dockerfile might take a few minutes (~10 minutes)**.

## Speed up Docker build - (Linux only)
Linux users can speed up the build process. Open [Dockerfile](./Dockerfile): modify `FROM --platform=linux/amd64 ubuntu:20.04` to `FROM ubuntu:20.04`. 
The `--platform=linux/amd64` has been added because new macOS versions did not support the installation of .NET-8 tools, without this specific flag. 



