## cisco_catc_commandrunner

## Catalyst center command runner functionality to find cdp neighbors
Cisco Catalyst Center managing your network devices can be queried to find out cdp neighbors easily without ssh to individual devices. Catalyst center keeps
track of all devices and command runner api allows to run commands on all those devices. This code shows how to achieve same. This code works against Catalyst Center release 2.3.7.9. 

## Business Challenge
Find out all cdp neighbors on scale. Example: PnP will have those neigbor device that can be onboarded from neigbor list that is generated. Like - IE3400.

## Goal
Use command runner API to derive needed information from Catalyst Center directly. 

## Installation
Clone the repo
```bash
git clone https://github.com/CiscoCSS/catc_commandrunner
```
or Download as zip on your environment by clicking the option "code >> local >> Download as zip"

Go to your project folder
```bash
cd catc_commandrunner
```
Set up a Python venv First make sure that you have Python 3.8 installed on your machine. We will then be using venv to create an isolated environment with only the necessary packages.

## Pre-requisite
Python 3.13.3. If python is not installed, please follow:
[https://www.python.org/downloads/](https://www.python.org/downloads/)

▪ pip3 or pip installed. If pip3 is not installed, please follow instructions at: 
[https://pip.pypa.io/en/stable/installing/virtualenv](https://pip.pypa.io/en/stable/installing/virtualenv)(https://pip.pypa.io/en/stable/installing/virtualenv) installed 

▪ If virtualenv not installed already, install through bash$ pip3 install virtualenv. Follow this for further instructions:
[https://pypi.org/project/virtualenv/](https://pypi.org/project/virtualenv/) 

▪ git installed
▪ if git is not installed, please try referring: 
[https://git-scm.com/downloads](https://git-scm.com/downloads)  

▪ Operating System: Linux based OS or windows

## Setup

Install virtualenv via pip
```bash
python3 -m venv env3 
```

Activate virtual environment
```bash
source env3/bin/activate
```

Run the command below with pip or pip3
```bash
pip install --upgrade pip 
```

```bash
pip install -r requirements.txt
```

or

```bash
pip install --upgrade pip
```

```bash
pip install cryptography
```

```bash
pip install fernet
```


## Run Script

### Step 1. 
Modify dnac_config.py file. Change the variables below per your environment.

```python
DNAC_URL_REGION1 = '<<https://catalystcenteripaddress'>> Change this to your lab environment
DNAC_USER_REGION1 = '<<change this you username plain text>>'
DNAC_PASS_REGION1 = '<<change this your password plain text for same url region1>>'
LIMIT = 5    #you can change this 500 to scale up on how many devices it queries that api will accommodate, please check on your specific release and catalyst center api. 
```
Run - python `command_runner.py` and test, if it picks up all cdp neighbors on all devices and generates same. Validate. You 
can also modify the script and run it against a device family to get cdp neighbors. For troubleshooting purpose you can easily troubleshoot with device id level too.
Check the log file `cdp_run_timestamp.log`. Validate output against your environment for the runs. For troubleshooting, you can comment out -filename=f"cdp_run_{datetime.datetime.now().strftime(DATE_FORMAT)[:-3]}.log" line from command runner.py file then logs will be writing at your console level.

**Recommend:** Extensive testing in your lab against all scenarios. Check if it picks up all devices and it's associated neighbors and tweak where needed. 

**Cisco Sample Code License, Version 1.1**
These terms govern this Cisco Systems, Inc. (“Cisco”), example or demo source code and its associated documentation (together, the “Sample Code”). By downloading, copying, modifying, compiling, or redistributing the Sample Code, you accept and agree to be bound by the following terms and conditions (the “License”). If you are accepting the License on behalf of an entity, you represent that you have the authority to do so (either you or the entity, “you”). Sample Code is not supported by Cisco TAC and is not tested for quality or performance. This is your only license to the Sample Code and all rights not expressly granted are reserved.

1. LICENSE GRANT: Subject to the terms and conditions of this License, Cisco hereby grants to you a perpetual, worldwide, non-exclusive, non-transferable, non-sublicensable, royalty-free license to copy and modify the Sample Code in source code form, and compile and redistribute the Sample Code in binary/object code or other executable forms, in whole or in part, solely for use with Cisco products and services. For interpreted languages like Java and Python, the executable form of the software may include source code and compilation is not required.

2. CONDITIONS: You shall not use the Sample Code independent of, or to replicate or compete with, a Cisco product or service. Cisco products and services are licensed under their own separate terms and you shall not use the Sample Code in any way that violates or is inconsistent with those terms (for more information, please visit: www.cisco.com/go/terms ).

3. OWNERSHIP: Cisco retains sole and exclusive ownership of the Sample Code, including all intellectual property rights therein, except with respect to any third-party material that may be used in or by the Sample Code. Any such third-party material is licensed under its own separate terms (such as an open source license) and all use must be in full accordance with the applicable license. This License does not grant you permission to use any trade names, trademarks, service marks, or product names of Cisco. If you provide any feedback to Cisco regarding the Sample Code, you agree that Cisco, its partners, and its customers shall be free to use and incorporate such feedback into the Sample Code, and Cisco products and services, for any purpose, and without restriction, payment, or additional consideration of any kind. If you initiate or participate in any litigation against Cisco, its partners, or its customers (including cross-claims and counter-claims) alleging that the Sample Code and/or its use infringe any patent, copyright, or other intellectual property right, then all rights granted to you under this License shall terminate immediately without notice.

4. LIMITATION OF LIABILITY: CISCO SHALL HAVE NO LIABILITY IN CONNECTION WITH OR RELATING TO THIS LICENSE OR USE OF THE SAMPLE CODE, FOR DAMAGES OF ANY KIND, INCLUDING BUT NOT LIMITED TO DIRECT, INCIDENTAL, AND CONSEQUENTIAL DAMAGES, OR FOR ANY LOSS OF USE, DATA, INFORMATION, PROFITS, BUSINESS, OR GOODWILL, HOWEVER CAUSED, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

6. DISCLAIMER OF WARRANTY: SAMPLE CODE IS INTENDED FOR EXAMPLE PURPOSES ONLY AND IS PROVIDED BY CISCO “AS IS” WITH ALL FAULTS AND WITHOUT WARRANTY OR SUPPORT OF ANY KIND. TO THE MAXIMUM EXTENT PERMITTED BY LAW, ALL EXPRESS AND IMPLIED CONDITIONS, REPRESENTATIONS, AND WARRANTIES INCLUDING, WITHOUT LIMITATION, ANY IMPLIED WARRANTY OR CONDITION OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, NON-INFRINGEMENT, SATISFACTORY QUALITY, NON-INTERFERENCE, AND ACCURACY, ARE HEREBY EXCLUDED AND EXPRESSLY DISCLAIMED BY CISCO. CISCO DOES NOT WARRANT THAT THE SAMPLE CODE IS SUITABLE FOR PRODUCTION OR COMMERCIAL USE, WILL OPERATE PROPERLY, IS ACCURATE OR COMPLETE, OR IS WITHOUT ERROR OR DEFECT.

7. GENERAL: This License shall be governed by and interpreted in accordance with the laws of the State of California, excluding its conflict of laws provisions. You agree to comply with all applicable United States export laws, rules, and regulations. If any provision of this License is judged illegal, invalid, or otherwise unenforceable, that provision shall be severed and the rest of the License shall remain in full force and effect. No failure by Cisco to enforce any of its rights related to the Sample Code or to a breach of this License in a particular situation will act as a waiver of such rights. In the event of any inconsistencies with any other terms, this License shall take precedence.

Last updated 2025. Modify code to fit your environment. 

## Disclaimer
This document contains guidance based on Cisco’s recommended practices. You remain responsible for determining whether to employ this guidance, whether it fits your network design, business needs, and whether the guidance complies with laws, including any regulatory, security, or privacy requirements applicable to your business.
