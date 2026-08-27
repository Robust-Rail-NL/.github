# Robust Rail NL
An open-source platform for development and research on the Train Unit Shunting Problem with Service task Scheduling.

The organization contains six core repositories:
- [robust-rail-generator](https://github.com/Robust-Rail-NL/robust-rail-generator): for generating instances
- [robust-rail-solver](https://github.com/Robust-Rail-NL/robust-rail-solver): for solving instances with local search
- [robust-rail-planner](https://github.com/Robust-Rail-NL/robust-rail-planner): for solving instances with AI planning
- [robust-rail-evaluator](https://github.com/Robust-Rail-NL/robust-rail-evaluator): for evaluating plans
- [robust-rail-visualizer](https://github.com/Robust-Rail-NL/robust-rail-visualizer): for visualizing plans
- [robust-rail-general](https://github.com/Robust-Rail-NL/robust-rail-general): This repository contains all the data, experimental setups, as well as precompiled images of the other repositories to easily run them on different machines.

### Installation
We recommend keeping all repositories in one main project folder

```bash
mkdir Robust-Rail-NL
cd Robust-Rail-NL
```


## How to Use? 

All tools can be used separately. However, a typical process would be as follows:

1) Generate a scenario with [**robust-rail-generator**](https://github.com/Robust-Rail-NL/robust-rail-generator)
    * *Input*:
        * Location file
        * Configuration for custom scenario, or random scenario generation

    * *Output*:
        * Scenario file compatible with **robust-rail-solver** and **robust-rail-planner**

2) Test the correctness of the scenario and location files with the **robust-rail-evaluator** - [CompatibilityTest.cpp](https://github.com/Robust-Rail-NL/robust-rail-evaluator/blob/main/cTORSTest/CompatibilityTest.cpp)
    *  *Input*: 
        * Location, Scenario, Plan (provide empty-path)

    * *Output*:
        * Tells if the Location is correct and the Scenario does not show absurd errors related to the first actions

3a) Create a plan with the [**robust-rail-solver**](https://github.com/Robust-Rail-NL/robust-rail-solver)
    * *Input*:
        * Scenario and Location file
    * *Output*:
        * Plan file in JSON (scheduled plan with all the actions)
        
3b) Create a plan with the [**robust-rail-planner**](https://github.com/Robust-Rail-NL/robust-rail-planner)
    * *Input*:
        * Scenario and Location file
    * *Output*:
        * Plan file  in JSON (scheduled plan with all the actions)

4) Evaluate plan with [**robust-rail-evaluator**](https://github.com/Robust-Rail-NL/robust-rail-evaluator)
     *  *Input*: 
        * Location, Scenario, Plan

    * *Output*:
        * Tells if the Plan is valid

5) Visualize plan with [**robust-rail-visualizer**](https://github.com/Robust-Rail-NL/robust-rail-visualizer)
     *  *Input*: 
        * Location, Scenario, Plan

    * *Output*:
        * Shows the plan sequentially in a local host environment=

## Valid scenarios, locations, and plan data 
The repository [**robust-rail-general**](https://github.com/Robust-Rail-NL/robust-rail-general) stores the configurations, scenarios, locations, plans, and evaluation results.

