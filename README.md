![Switch Logo](docs/switch_white_logo.svg)

# Josev - Joint Operating System for EV chargers

Josev Community is the open source version of Josev - an operating system for the V2G charging stations.

Josev (Joint Operating System for EV chargers) is an open source stack containing modules that, together,
function as the brain of a charging station, enabling Vehicle-to-Grid (V2G) communication and pushing forward EV
adoption by reducing interoperability issues.

Josev was designed with modularity at heart. It is based in modern technologies, with the majority of the code
currently in Python.

## What does the project include?

The Josev Community version, at the moment, is the compilation of the following modules, which individually live in
their own repository:

- `iso15118`: https://github.com/SwitchEV/iso15118

* `slac`: https://github.com/SwitchEV/slac

The aforementioned repos include: installation and run steps; examples; and a CI/CD based on GitHub actions that
will run tests and perform code quality checks. Once a new release is made, a Python package is published to the
public pypi server.

The `iso15118`repo provides the following services and features:

|                     | AC  | DC  | AC BPT | DC BPT | DC ACDP | DC ACDP BPT | WPT | EIM |   PnC   |
| ------------------- | :-: | :-: | :----: | :----: | :-----: | :---------: | :-: | :-: | :-----: |
| ISO 15118-2 [^1]    | ✅  | ✅  |   -    |   -    |    -    |      -      |  -  | ✅  |   ✅    |
| ISO 15118-20 [^2]   | ✅  | ✅  |   ✅   |   ✔️   |   ❌    |     ❌      | ❌  | ✅  | ✅ [^5] |
| DIN SPEC 70121 [^4] |  -  | ✅  |   -    |   -    |    -    |      -      |  -  |  ✅   |    -    |

"✅" -Fully Supported

"✔" -Partially Supported

"❌" -Not Supported at the moment

"-" -Not Applicable

## Why name the repos `iso15118` and `slac`?

The `iso15118` repo, despite the name, also includes support for DIN SPEC 70121.
Switch believes that the way forward to a future where a secure, reliable and seamless charging experience can be
achieved is by pushing the ISO 15118 standards. For that reason we instigate people to adopt the ISO 15118 over DIN SPEC 70121. However, we do understand the current market needs and the fact that there are thousands of
Electric Vehicles (EVs) which only support DIN SPEC (the so-called "legacy EVs"); thus we do provide support
for DIN SPEC, but we restrain ourselves from promoting it.

Why do we have two repos, one for the high-level communication (the `iso15118`) and another for `slac`? The first
reason is to mimic a microservices architecture where future updates are atomic and smaller. Secondly, it's due to
separation of concerns, as `slac` deals with the Physical and Data link layers (OSI layers 1 and 2), whilst `iso15118`
deals with the Network, Transport, Session, Presentation and Application layers of the OSI stack (layers 3-7).
Thirdly, the names match the language used in the community where `iso15118`is generally used to discuss high-level
communication topics and `slac` to describe the protocol defined in ISO 15118-3. [^3].

## How to spin it up?

As the project is a collection of modules, each module can be independently used. As the `iso15118` modules requires
some integration from the user side, specifically with the EVSE/EVCC controller part, it makes no sense to create a
set of commands here to fire up both the `iso15118` and `slac` modules.
Thus, to use the project, please follow the instructions specified in each of the repos.

## Caveats and shortcomings

As mentioned, the project includes unit testing for each published module, but the coverage of the tests needs to be
improved.
To compensante that shortcoming, the system was subject to intense field-testing. Specifically, we tested the project
successfully in the following international and widely recognized events:

- [CharIN Testivals](https://www.charin.global/events/global-testivals/)
- [Vector vTESTival](https://www.vector.com/de/de/events/global-de-en/2022/vector-e-mobility-symposium-2022/#c284443)

The system was also subject to conformance testing for ISO 15118.
The tests were done using the Keysight conformance test system (comTEST), containing the
[SL1459A EVSE DIN 70122 & ISO 15118-4/-5:2018 AC/DC & PNC Conformance Bundle](https://www.keysight.com/gb/en/assets/3120-1491/data-sheets/SL14XXA-Scienlab-Test-Case-Library-TTCN-3.pdf)

A list of the tests that the SUT (System Under Test) was subject to, including the tests that the system currently
didn't pass, can be found in the tests directory.

## What are the next goals?

The stack will keep growing, and it's our goal to support all the features described by the ISO 15118-2 and -20 chapters.
In the upcoming months, we will focus on continuously battle-testing the stack and solidifying all the AC/DC and
corresponding BPT scenarios.
For now, ACDP and WPT won't be our top priority, but this may change depending on the market needs.

As initially mentioned, our stack is mainly based in Python, and despite Python not being the best performing language,
after several interoperability tests, we detected no timing performance issues or any indication that would violate
the requirements specified by the standard.

Nevertheless, we believe the solution we offer to the community must be robust, reliable, safe, easily maintainable and
easily distributable. For those reasons, it's our intention to partially or totally convert our stack to Rust, a strongly
statically typed, multi-paradigm programming language focussing on safety and performance, suitable for embedded devices.

At first, we will provide this solution as part of our fee-paying Josev Professional edition, but we may also open source
it later. Okay, so, wait - now you may be asking yourself, "Josev Professional? What's that?" Read on.

## Josev Professional Edition

Yes, we are here to support the e-mobility community with our solutions, and we pride ourselves on open sourcing as much
as possible. At the same time, we want to target a segment of the industry with specific business requirements,
eg integrating an interface for a OEM power electronics module that uses CAN, a module to interface with a specific
RFID reader or through ModBus with a smart meter. And to answer those needs, we want to provide a dedicated and
professional offer, and that offer is "Josev Professional" (or Josev Pro for short).

Josev Pro inclues all that Josev Community Edition has plus:

- OCPP 2.0.1
- REXI - A Rust version of the EXI en/decoder, which is at least x100 faster than the available open source solutions
  and has ISO 15118-20 support (check [here](docs/rexi_performance.png) )
- An Over-the-Air (OTA) update service - Allowing your product to receive the latest release versions of Josev with new
  features and possible fixes
- An MQTT message broker and well defined API to interact with OEM-specific code (and between the ISO 15118, SLAC, and OCPP 2.0.1 modules)
- RFID module interface
- Power Electronics module interface
- Lifetime support from our Switch engineers and specialists
- And more...

Josev Pro requires a Linux based OS and runs in all major archs: `armv7`, `armv8`, `x86_64`.

If you are interested and want to know more, we'd love to talk, so please contact us here today:
<email, booking link to Stewart..>

## How to Contribute?

...

## Questions/Issues

For generic questions regarding Josev as a whole we invite the user to create an issue in this repository.
To report an issue or raise a question related to a specific module/service, we encourage you to create an issue
directly in the repository to which the question applies. For example, if you found a bug while running the `iso15118`
repo, then, please, open an issue in that repo.

## License

Copyright [2022] [Switch-EV]

All Switch content and modules are under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

[^1]: https://www.iso.org/standard/55366.html
[^2]: https://www.iso.org/standard/77845.html
[^3]: https://www.iso.org/standard/59675.html
[^4]: https://standards.globalspec.com/std/9884003/DIN%20SPEC%2070121
[^5]: PnC in ISO 15118-20 requires TLS v1.3 and a new set of cryptography suites that still need to be implemented
[^6]: https://exificient.github.io/
