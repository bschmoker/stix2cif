###############################################################################
#Copyright (c) 2014 Carnegie Mellon University.
#
#All Rights Reserved.
#
#Redistribution and use in source and binary forms, with or without 
# modification, are permitted provided that the following conditions are met:
#
#1. Redistributions of source code must retain the above copyright notice, this 
# list of conditions and the following acknowledgments and disclaimers.
#
#2. Redistributions in binary form must reproduce the above copyright notice, 
# this list of conditions and the following acknowledgments and disclaimers in 
# the documentation and/or other materials provided with the distribution.
#
#3. Products derived from this software may not include Carnegie Mellon 
# University, "SEI and/or Software Engineering Institute" in the name of such 
# derived product, nor shall Carnegie Mellon University, "SEI and/or Software
# Engineering Institute" be used to endorse or promote products derived from 
# this software without prior written permission. For written permission, 
# please contact permission@sei.cmu.edu.
#
#ACKNOWLEDMENTS AND DISCLAIMERS:
#
#Copyright 2014 Carnegie Mellon University
#
#This material is based upon work funded and supported by Department of 
# Homeland Security under Contract No. FA8721-05-C-0003 with Carnegie 
# Mellon University for the operation of the Software Engineering Institute,
# a federally funded research and development center sponsored by the United 
# States Department of Defense.
#
#Any opinions, findings and conclusions or recommendations expressed in this 
# material are those of the author(s) and do not necessarily reflect the views
# of Department of Homeland Security or the United States Department of Defense.
#
#References herein to any specific commercial product, process, or service by 
# trade name, trade mark, manufacturer, or otherwise, does not necessarily 
# constitute or imply its endorsement, recommendation, or favoring by Carnegie
# Mellon University or its Software Engineering Institute.
#
#NO WARRANTY. THIS CARNEGIE MELLON UNIVERSITY AND SOFTWARE ENGINEERING 
# INSTITUTE MATERIAL IS FURNISHED ON AN "AS-IS" BASIS.
# CARNEGIE MELLON UNIVERSITY MAKES NO WARRANTIES OF ANY KIND, EITHER EXPRESSED 
# OR IMPLIED, AS TO ANY MATTER INCLUDING, BUT NOT LIMITED TO, WARRANTY OF 
# FITNESS FOR PURPOSE OR MERCHANTABILITY, EXCLUSIVITY, OR RESULTS OBTAINED FROM
# USE OF THE MATERIAL.
#CARNEGIE MELLON UNIVERSITY DOES NOT MAKE ANY WARRANTY OF ANY KIND WITH RESPECT
# TO FREEDOM FROM PATENT, TRADEMARK,
# OR COPYRIGHT INFRINGEMENT.
#
#This material has been approved for public release and unlimited distribution.
#
#Carnegie Mellon(R) is registered in the U.S. Patent and Trademark Office by 
# Carnegie Mellon University.
#
#DM-0001329
###############################################################################

== GENERAL INFORMATION ==

Name: Stix2Cif
Version: 1.0.0
PL: Python2.6
OS: RHEL 6


== DESCRIPTION ==

This is a plug-in for CIF that consists of a Python module. It parses 
STIX/Cybox documents into JSON CIF Feed files with corresponding configuration
files for each source document and feed it to CIF.


== MAIN FUNCTIONALITY ==

Python module
-------------------
-	Monitors drop-off directory for XML files
-	Parses STIX/CyBox documents and maps keys to CIF parameters 
-	Creates a separate JSON object for each Indicator
-	Builds a JSON Feed file and CIF Feed configuration file from each source
	XML file
-	Allows to change configuration of CIF Feed 
-	Logs in activities
== INSTUCTIONS ==

Python module
-------------------

To install CIF dependencies:
```
apt-get install automake libtool; 
sudo cpan Google::ProtocolBuffers; 
git clone https://github.com/collectiveintel/cif-v1.git;  
cd cif-v1
./rebuild.sh 
sudo useradd cif; 
./configure && make && sudo make install
```

To install python dependencies:
`pip install -r requirements.txt`


This module requires configuration file ? stix2cif_config.cfg. You can pass the 
full path as input argument, or hard-code the path in the module.

The configuration file allows to set:
- Home directory of the Stix2Cif plug-in
- Home directory of the CIF
- Drop-off of STIX files directory
- CIF configuration file
- CIF call command
- Stix2Cif run directory (for temp files)
- CIF fields/parameters list, order and some defaults
- CIF Feed configuration file template
- Stix2Cif logger configuration


The Stix2Cif runs from command line.

Usage:
  stix2cif [?c <cinfug>]
  stix2cif [--version]
  stix2cif [-h | --help]

Options:
  --version            Show version.
                           [default: 1.0.0]
  -h --help            Show this screen.
  -c				Configuration file to use
					[default: ./stix2cif_config.cfg]

== OTHER ==

Contributor: Nataliya A. Shevchenko, SEI CERT
Date: May 15th, 2014
