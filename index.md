---
layout: default
title: BIC-MNI Software repository
---
## Contents:
* [MINC Toolkit](#MINC-Tool-Kit)
  * [MINC Toolkit versions](#notes-about-versions)
  * Version 1 [Version 1.0.08](#version-10081008-currently-stable)
  * Version 2 [Version 1.9.11](#v2-version-19111911)
  * [Virtual Machine](#virtual-machine)
  * [Data files and models](#data-files-and-models)
  * [Previous versions](#previous-versions)
  * [Installing](#installing)
    * [On Debian/Ubuntu](#on-debianubuntu)
    * [On CentOS / OpenSuse / Fedora](#on-centos--opensuse--fedora)
    * [On MacOS X 10.7 and 10.9](#on-macos-x-107-and-109)
  * [Using](#using)
  * [Running test suite](#running-test-suite)
  * [Building from the source](#building-from-the-source)
* [Additional software ported to support MINC file format](#additional-software-ported-to-support-minc-file-format)
  * [ITK-SNAP 3.2](#itk-snap-32)


This software repository contains open-source tools developed at the McConnell Brain Imaging Centre, Montreal Neurological Institute
The main documentation site for this repository is located at [wikibooks](https://en.wikibooks.org/wiki/MINC)

Also, concise man pages for various minc tools are located at [bic-mni.github.io/man-pages](http://bic-mni.github.io/man-pages/)

## Support
Contact @vfonov, @andrewjanke or @rdvincent if you have any questions

## MINC Tool Kit
This toolkit contains most of the commonly used minc tools in one precompiled 32 and 64bit binary packages of Debian, Ubuntu, RedHat and Mac OS X.
It includes most of the standard minc tools, Display, Register and a  basic image processing pipeline based on the one developed for NIHPD
project (standard_pipeline.pl) Everything is currently installed in /opt/minc , to avoid conflict with standard /usr/local/bic location.

### Notes about versions
* **1.0.XX** - is a stable version that still includes all the latest versions of the minc tools, and several programs based on ITK 3.20. 
  The standard minc-based programs are kept up-to date, but new experimental software is not included. Use this version if you need 
  only basic minc tools (i.e register/Display/xdisp) or you are running a legacy image processing pipeline that does not require new tools.
* **1.9.XX** - includes the same standard minc-tools as version 1.0.XX, but sometimes with updated parameters (minctracc so far is the only such program). 
  Also includes new experimental software based on ITK 4.XX and latest versions of ANTS,Elastix and C3D. 
  Use this version if you are interested in the latest versions of ANTs and Elastix or running more recent software pipelines 
  (in particular patch-based segmentation).

### [Version 1.0.08](#1.0.08) (currently stable)
- 64 bit tools
  * Ubuntu
    * [1.0.08 Ubuntu 10.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_10.04-x86_64.deb)
    * [1.0.08 Ubuntu 12.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_12.04-x86_64.deb)
    * [1.0.08 Ubuntu 14.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_14.04-x86_64.deb)
    * [1.0.08 Ubuntu 15.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_15.04-x86_64.deb)
  * Debian
    * [1.0.08 Debian-6.0.10](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Debian_6.0.10-x86_64.deb)
    * [1.0.08 Debian-7.3](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Debian_7.3-x86_64.deb)
    * [1.0.08 Debian-8.0](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Debian_8.0-x86_64.deb)
  * RPM based
    * [1.0.08 CentOS 6.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.08-20160205-CentOS_6.7-x86_64.rpm)
    * [1.0.08 Fedora 20](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.08-20140603-Fedora_20-x86_64.rpm)
    * [1.0.08 openSUSE 13.2](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.0.08-20160205-openSUSE-project_13.2-x86_64.rpm)
  * MacOS X 
    * [1.0.08 MacOS X 10.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-1.0.08-20160205-Darwin-10.7-x86_64.dmg)
    * [1.0.08 MacOS X 10.11](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-1.0.08-20160205-Darwin-10.11-x86_64.dmg)
- 32 bit tools **Caveat Emptor** Unfortunately, currently `mincbeast` is unable to run in 32bit mode properly, so `standard_pipelene.pl` will fail (and the test-suite will also fail).
  * Ubuntu
    * [1.0.08 Ubuntu 10.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_10.04-i686.deb) 
    * [1.0.08 Ubuntu 12.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Ubuntu_12.04-i686.deb)
  * Debian
    * [1.0.08 Debian-7.8](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.0.08-20160205-Debian_7.8-i686.deb)
- Source code
  * minc-toolkit complete source archive
    * [1.0.08 tar.gz archive](http://packages.bic.mni.mcgill.ca/minc-toolkit/minc-toolkit-1.0.08-20160205.tar.bz2)
- Testsuite (under development)
    * [0.1.3 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-testsuite-0.1.3-20131212.deb)
    * [0.1.3 CentOS 6.4](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-testsuite-0.1.3-20131212.rpm) 
    * [0.1.3 MacOS X 10.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-testsuite-0.1.3-20131212.dmg)

### V2 [Version 1.9.11](#1.9.11) 
This version includes ITK-4.9, latest version of Elastix, ANTs and C3D - all with minc support. **WARNING** some basic tools produce results incompatible with version 1.00.XX Test-suite will fail due to changes in minctracc
All files will be installed into /opt/minc-itk4 in order to co-exist with version 1 of minc-toolkit

* 64 bit tools
  * Ubuntu
    * [1.9.11 Ubuntu 10.04](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_10.04-x86_64.deb) 
    * [1.9.11 Ubuntu 12.04](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_12.04-x86_64.deb)
    * [1.9.11 Ubuntu 14.04](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_14.04-x86_64.deb)
    * [1.9.11 Ubuntu 15.04](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_15.04-x86_64.deb)
  * Debian
    * [1.9.11 Debian-6.0.10](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Debian_6.0.10-x86_64.deb)
    * [1.9.11 Debian-7.3](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Debian_7.3-x86_64.deb)
    * [1.9.11 Debian-8.0](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Debian_8.0-x86_64.deb)
  * Redhat-based
    * [1.9.11 CentOS 6.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.11-20160202-CentOS_6.7-x86_64.rpm)
    * [1.9.11 Fedora 20](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.11-20160202-Fedora_20-x86_64.rpm)
    * [1.9.11 OpenSUSE 13.2](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/minc-toolkit-1.9.11-20160202-openSUSE-project_13.2-x86_64.rpm)
  * MacOS X
    * [1.9.11 MacOS X 10.11 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/minc-toolkit-1.9.11-20160202-Darwin-10.11-x86_64.dmg)
* 32 bit tools **Caveat Emptor** Unfortunately, currently `mincbeast` is unable to run in 32bit mode properly, so `standard_pipelene.pl` will fail 
  * Ubuntu
    * [1.9.11 Ubuntu 10.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_10.04-i686.deb) 
    * [1.9.11 Ubuntu 12.04 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Ubuntu_12.04-i686.deb) 
  * Debian
    * [1.9.11 Debian-7.8](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/minc-toolkit-1.9.11-20160202-Debian_7.8-i686.deb)
* Source code
  * minc-toolkit complete source archive
    * [1.9.11 tar.bz2 archive](http://packages.bic.mni.mcgill.ca/minc-toolkit/minc-toolkit-v2-1.9.11-20160202.tar.bz2)

### Virtual Machine

A virtual machine containing minc-toolkit, as well as a number of tools built upon it is available for download at [CoBrALab/MINC-VM](https://github.com/CobraLab/MINC-VM)
It is kept up to date with the latest releases of minc-toolkit and additional tools.

### Data files and models
These packages contain anatomical models needed for standard pipeline, all files are installed into `/opt/minc/share`

  * BEaST segmentation library, needed to run mincbeast software for brain extraction 
    * [1.1.0 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/beast-library-1.1.0-20121212.deb) 
    * [1.1.0 CentOS](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/beast-library-1.1.0-20121212.rpm)
    * [1.1.0 MacOS X](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/beast-library-1.1.0-20121212.dmg)
  * bic-mni-models  anatomical template library,  includes models from [ICBM 2009 template](http://www.bic.mni.mcgill.ca/ServicesAtlases/ICBM152NLin2009)
    * [0.1.1 Debian/Ubuntu](http://packages.bic.mni.mcgill.ca/minc-toolkit/Debian/bic-mni-models-0.1.1-20120421.deb)
    * [0.1.1 CentOS 6.4](http://packages.bic.mni.mcgill.ca/minc-toolkit/RPM/bic-mni-models-0.1.1-20120421.rpm)
    * [0.1.1 MacOS X 10.7](http://packages.bic.mni.mcgill.ca/minc-toolkit/MacOSX/bic-mni-models-0.1.1-20120421.dmg)
    
### Previous versions

Previous versions are archived in [http://packages.bic.mni.mcgill.ca/minc-toolkit/](http://packages.bic.mni.mcgill.ca/minc-toolkit/)

### Installing

#### On Debian/Ubuntu
* install dependencies: `sudo apt-get install libc6 libstdc++6 imagemagick perl`
* optional dependency is octave, which is currently used only by xfmavg script.
* download corresponding binary packages 
* run `sudo dpkg -i minc-toolkit-<version>.deb minc-toolkit-testsuite-<version>.deb bic-mni-models-<version>.deb beast-library-<version>.deb `. 
  Sometimes it will be necessary to run `sudo apt-get install -f` afterwards to install missing libraries.
* Visualization programs : register, display and ray_trace rely on working OpenGL , install appropriate drivers or software emulation `sudo apt-get install libgl1-mesa-glx libglu1-mesa`

#### On CentOS / OpenSuse / Fedora
* install dependencies: `sudo yum install glibc libstdc++ ImageMagick perl`
* install downloaded rpm packages 

#### On MacOS X 10.7 and 10.9 
* download and double click on  appropriate dmg file, the standard MacOS X installer will start
* install ImageMagick, either using [mac ports](https://www.macports.org/install.php) - preferred or [homebrew](http://brew.sh/)

### Using
* Version **1.0.XX (stable)**:
   source the environment in `/opt/minc/minc-toolkit-config.sh` for bash or `/opt/minc/minc-toolkit-config.csh` for tcsh 
* Version **1.9.XX (version 2 )**:
   source the environment in `/opt/minc-itk4/minc-toolkit-config.sh` for bash or `/opt/minc-itk4/minc-toolkit-config.csh` for tcsh 


### Running test suite
Test data is installed in `/opt/minc/share/testsuite/`.  To run the test, execute `/opt/minc/run_tests.sh <prefix>`, it will take around
an hour on  a modern PC, the output will be in `<prefix>/00200`  and `<prefix>/00201` and the log file will be saved in
`<prefix>/minc-toolkit-test-<date>.log`.  The results of the local test will be compared to a file containing the results from 
a baseline test to determine if the tools have been installed and run correctly. 

### Building from the source
Consult [minc-toolkit on github](https://github.com/BIC-MNI/minc-toolkit) or [minc-toolkit-v2 on github](https://github.com/BIC-MNI/minc-toolkit-v2) for details and to download latest version of the software.

## Additional software ported to support MINC file format

### ITK-SNAP 3.2
* MacOS X
  * [MacOS X 10.7 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/third-party/itksnap-3.4.0-20151130-MacOS-x86_64-qt4.dmg) - QT 4 version (doesn't support retina display)
  * [MacOS X 10.11 or later](http://packages.bic.mni.mcgill.ca/minc-toolkit/third-party/itksnap-3.4.0-20151130-MacOS-10.11-x86_64-qt5.dmg) - QT 5 version
