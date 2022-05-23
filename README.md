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

|              	| AC 	| DC 	| AC BPT 	| DC BPT 	| ACDP 	| WPT 	| EIM 	| PnC 	|
|--------------	|----	|----	|--------	|--------	|------	|-----	|-----	|-----	|
| DIN 70121    	|  - 	|  ✅ 	|    -   |    -   	|   -  	|  -  	|  ✅  	|     	|
| ISO 15118-2  	|  ✅ 	|  ✅ 	|    -   	|    -   	|   -  	|  -  	|  ✅  	|  ✅  	|
| ISO 15118-20 	|  ✅ 	|  ✅ 	|    ✅   	|   ❌  	|  ❌ 	| ❌ 	|  ✅  	|  ✅* 	|

* PnC in ISO 15118-20 requires TLS v1.3 and a new set of cryptography suites that still need to be implemented


# How to spin it up?

As the project is a collection of modules, each module can be independently used. As the [ISO 15118] modules requires some integration from the user side, specifically with the EVSE/EVCC controller part, it makes no sense to create a set of commands here to fire up both the [ISO 15118] and slac modules.
Thus, to use the project, please folow the instructions specified in each of the repos.
 


# What are some caveats and what are the next goals?

* Documentation 
* More Tests
* work on the currently unsupported features of ISO 15118-20


# How to Contribute?
...


# Questions/Issues
For generic questions regarding Josev as whole we invite the user to create an issue in this repository.
To report an issue or raise a question related to a specific module, we encorage you to create an issue directly in the repository where the question aplies. For example, if you found a bug while running the ISO 15118 repo, then, please, open an issue in that repo.


# License
Copyright [2022] [Switch-EV]

All Switch-EV content and modules are under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

