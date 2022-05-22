<p align="left"> <img src="https://komarev.com/ghpvc/?username=tropx&label=Profile%20views&color=0e75b6&style=flat" alt="tropx" /> </p>

# Josev - Joint Operating System for Seemless EV charging

The community version of Josev - An Operating System for the V2G charging Stations

Josev or Joint Operating System for Seemless EV charging is an open source stack containing modules that together function as the brain of a charging station, enabling V2G communication and pushing forward EV adoption, by reducing interoperability issues.

Josev was designed with modularity in its heart and is based in modern technologies, being the majority of the code in Python.


# What does the project includes?

Josev Community version at the moment is the compilation of the following modules which individually live in their own repository:

* ISO 15118 (name to be redefined): https://github.com/SwitchEV/iso15118
* SLAC - https://github.com/SwitchEV/slac

The aforementioned repos include installation and run steps, examples and a CI/CD based on GitHub actions that will run the tests and performs code quality checks.


The [ISO 15118] repo provides the following features:

|              |         AC         |         DC         |       AC BPT       | DC BPT | ACDP | WPT | EIM                | PnC                  |
|:------------:|:------------------:|:------------------:|:------------------:|:------:|------|-----|--------------------|----------------------|
| DIN 70121    | -                  | :heavy_check_mark: | -                  | -      | -    | -   | :heavy_check_mark: |                      |
| ISO 15118-2  | :heavy_check_mark: | :heavy_check_mark: | -                  | -      | -    | -   | :heavy_check_mark: | :heavy_check_mark:   |
| ISO 15118-20 | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :x:    | :x:  | :x: | :heavy_check_mark: | :heavy_check_mark: * |


# How to spin it up?


# What are some caveats and what are the next goals?



The [ISO 15118]



# How to Contribute?


# Questions/Issues
For generic questions regarding Josev as whole we invite the user to create an issue in this repository.
To report an issue or raise a question related to a specific module, we encorage you to create an issue directly in the repository where the question aplies. For example, if you found a bug while running the ISO 15118 repo, then, please, open an issue in that repo.


# General License


