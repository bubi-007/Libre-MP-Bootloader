
# Libre-MP-Bootloader

### Free interoperation of non-3D Robotics Pixhawk boards with the APM Mission Planner

May 3, 2014

    What Anderson envisages -- more of the same but with greater diversity and
    competition -- may come to pass. But to set the threshold for the third
    industrial revolution so low just because someone somewhere forgot to
    regulate A.T. & T. (or Google) seems rather unambitious.

    - Evgeny Morozov, "Making It", The New Yorker, Jan 13 2014

## What is this?

At the time of this writing, 3D Robotics distributes the open source [APM
Mission Planner][mp] with a restriction that prevents uploading firmware
open-hardware Pixhawk boards which were not manufactured by 3D Robotics.

[mp]: http://planner.ardupilot.com/

This is an alternative bootloader for non-3DR Pixhawk boards that bypasses the
restriction built into the Mission Planner. Any Pixhawk board with this
bootloader will report the serial number and COA (Certificate of Authenticity)
data given by an authentic 3DR Pixhawk board.

## Why are you doing this?

The restriction in the APM Mission Planner binary restricts user freedom to
interoperate between open source hardware and open source software. In my
opinion, this restriction is contrary to the spirit of open source.

The authentication features implemented in the APM Mission Planner do not
violate the open source license of that software. However almost all APM
Mission Planner users expect to use the software by downloading the official
binary (distributed on [ardupilot.com](http://ardupilot.com/downloads/), a
website owned by 3D Robotics). This official version, upon detecting a
non-authentic 3DR Pixhawk, will refuse to upload firmware to the Pixhawk.

The Mission Planner is open source software, and the authenticity check may be
bypassed by changing a single line of the source code. Under the software
license, others are free to distribute binaries and source for the Mission
Planner with this modification. However, this forces users to either compile
their own Mission Planner, which is a complex technical operation out of scope
for most users, or to trust that a binary version provided by a third party
contains only the required modification and not any extra malicious code.

This bootloader sidesteps the restrictions of the official Mission Planner
binary. I do not believe Mission Planner users should be required to build
their own binaries, or trust binaries from an untrustworthy third party, in
order to have freedoms *within the spirit of open hardware and open source
software*. You are welcome to disagree with my beliefs or my own definition of
"the spirit of open source".

## What about the support 3DR gives the development team?

3D Robotics has supported the APM, Pixhawk, and APM Mission Planner open source
projects with both direct financial support of project maintainers, and provided
free prototype and production hardware to many of the development team members.
3DR's support of the developers has been beneficial to the quality of software
and hardware provided by these projects. At this time and to the best of my
knowledge, no other manufacturers of Pixhawk hardware has provided support,
directly or indirectly, to the maintainers or contributors of any of these open
source projects.

While 3D Robotics has done an enormous amount to support the developer team,
that support has thus far not come with any "strings attached". Open source
contributors paid or otherwise supported by 3DR retain copyright of their work,
and all of that work is available under the open source license of the parent
project (GPL, BSD, or CC-BY-SA, where applicable).

This is the first time I've seen 3D Robotics use their support of a open source
contributors to impose restrictions on competing hardware manufacturers.
While the Mission Planner project maintainers have every right to follow 3DR's
direction to include this restriction, 3DR's directions are *bad stewardship* of
the open source community, because they *reduce user freedoms* for their own
gain. This precedent reduces the legitimacy of the entire family of 3DR
supported open source projects, and ought to make contributors and competitors
alike less comfortable supporting these projects. To restore community trust,
3DR should remove the authenticity restrictions from the Mission Planner.

## How do I use this?

You will need to build it and reflash the Pixhawk bootloader using a JTAG
debugger. If you don't already know exactly what that means, the upgrade isn't
for you - it entails having the correct toolchain on your computer, having
access to a JTAG debugger and either using a solderless connection jig or
soldering a surface mount JTAG pin header to the Pixhawk board.

This bootloader may be flashed at the factory by a non-3DR Pixhawk manufacturer,
as an alternative to flashing the standard Pixhawk bootloader.  Users of a board
with this bootloader will not need to use an unofficial distribution of the APM
Mission Planner for firmware upgrade.

## Why the name "Libre-MP-Bootloader"

This is a fork of the PX4 open source project bootloader. I want to emphasize
that the official bootloader, nor any of the PX4 project's firmware upload
software, uses the board authentication features to restrict use of any hardware
or software.

Lorenz, the PX4 project lead, pointed out that the project name may reflect
poorly on their project. This was not my intention, and I regret any confusion
this causes.

The official bootloader reports the values true values of the serial
number and one-time programmable (OTP) memory on the STM32F4 chip. This
bootloader lies when reporting those fields, instead reporting values
from a 3DR-manufactured Pixhawk board purchased by the author.

## Who are you? What is your connection to APM?

I'm Pat Hickey, a software developer from Portland, Oregon. In the past I served
as one of the maintainers of the ArduPilot (APM) open source project. I became
involved in the APM project in mid 2011, and my last commit to the APM project
was in Feburary 2013.

During that time, my major contributions were adding hardware support for the
APM2 board, and the AP_HAL Hardware Abstraction Layer which permitted hardware
support of non-Arduino based boards, which included PX4 project hardware, the
second generation of which is the Pixhawk.

I have collaborated with 3DR on many of hardware and software projects in the
past. I've considered all of those collaborations to be positive and do not wish
3DR badly.  I have never received direct financial support from 3DR, but they
have sent me a bunch of free hardware and paid my travel expenses to speak at
DroneCon in 2013.

Currently, I'm the engineering lead of the [SMACCMPilot Project][sp], a research
project building high assurance open-source autopilot software. SMACCMPilot
uses open source software derived from the APM open source project and the PX4
project. It is research software and not intended to provide a user alternative
to the APM project software at this time.

[sp]: http://smaccmpilot.org

## Are these opinions the opinions of your employer? Are RT's endorsements?

lol, no. All opinions on this page are my own. Please send all hate mail to
`pat@moreproductive.org`.

