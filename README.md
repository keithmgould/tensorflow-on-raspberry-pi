# Installing TensorFlow on Raspberry Pi 3

## Donate to Original Author

I (Keith) am not asking for donations, but the original author is. Here is his message:

If you find the binaries and instructions in this repository useful, [please consider donating to help keep this repository maintained](https://pledgie.com/campaigns/33260). It takes hours of work to compile each new version of TensorFlow, in addition to time spent responding to issues and pull requests.

## Intro

If you're looking to run [fully featured TensorFlow](https://github.com/tensorflow/tensorflow) or [Bazel](https://github.com/bazelbuild/bazel) on a Raspberry Pi 3, you're in the right place.

**This repo includes the whl binary so you don't have to go through the pain of compiling from scratch...**

This repo also contains step-by-step instructions for installing TensorFlow 1.5.1 from source using Bazel (which is also compiled from-scratch) on Python 3.5.

_As a quick note, if you're looking for officially supported TensorFlow/Raspberry Pi functionality, you can also check out using the [Makefile contrib module](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/contrib/makefile). It builds a static C++ library instead of the standard Python library, but is very powerful._

## Installing from Pip3

**Note: These are unofficial binaries (though built from the minimally modified official source), and thus there is no expectation of support from the TensorFlow team. Please don't create issues for these files in the official TensorFlow repository.**

This is the easiest way to get TensorFlow 1.5.1 onto your Raspberry Pi 3 for Python 3.5. Note that currently, the pre-built binary is targeted for Raspberry Pi 3 running Raspbian 9.0 ("Stretch"), so this may or may not work for you. The specific OS release is the following:

First, install the dependencies for TensorFlow:

```shell
sudo apt-get update
sudo apt-get install python3-pip python3-dev
```

Next, download the wheel file from this repository and install it:

```shell
wget https://github.com/keithmgould/tensorflow-on-raspberry-pi/releases/download/v1.5.1/tensorflow-1.5.1-cp35-cp35m-linux_armv7l.whl

sudo pip3 install tensorflow-1.5.1-cp35-cp35m-linux_armv7l.whl
```

Finally, we need to reinstall the `mock` library to keep it from throwing an error when we import TensorFlow:

```shell
sudo pip3 uninstall mock
sudo pip3 install mock
```

And that should be it!

## Building from Source

[_Step-by-step guide_](GUIDE.md)

Ugh, so it looks like the wheel I made was in tmp and is gone :( and I'm not going to make it again, BUT I've updated the guide so its pretty easy (but time consuming) for you to build by source. 

See the [step-by-step guide here](GUIDE.md). **Warning: it takes a while.**

## Non-Raspberry Pi Model 3 builds

There are numerous single-board computers available on the market, but binaries and build instructions aren't necessarily compatible with what's available in this repository. This is a list of resources to help those with non-RPi3 (or RPi 2) computers get up and running:

* ODROID
    * [Issue thread for ODROID](https://github.com/samjabrahams/tensorflow-on-raspberry-pi/issues/41)
		* [NeoTitans guide to building on ODROID C2](https://www.neotitans.net/install-tensorflow-on-odroid-c2.html)

## Credits

While the final pieces of grunt work were done primarily by @samjabrahams and @petewarden, this effort has been going on for almost as long as TensorFlow has been open-source, and involves work that spans multiple months in separate codebases. This is an incomprehensive list of people and their work Sam ran across while working on this.

The majority of the source-building guide is a modified version of [these instructions for compiling TensorFlow on a Jetson TK1](http://cudamusing.blogspot.com/2015/11/building-tensorflow-for-jetson-tk1.html). Massimiliano, you are the real MVP. _Note: the TK1 guide was [updated on June 17, 2016](http://cudamusing.blogspot.com/2016/06/tensorflow-08-on-jetson-tk1.html)_

@vmayoral put a huge amount of time and effort trying to put together the pieces to build TensorFlow, and was the first to get something close to a working binary.

A bunch of awesome Googlers working in both the TensorFlow and Bazel repositories helped make this possible. In no particular order: @vrv, @damienmg, @petewarden, @danbri, @ulfjack, @girving, and @nlothian

_Issue threads of interest:_

* [Initial issue for building Bazel on ARMv7l](https://github.com/bazelbuild/bazel/issues/606)
* [First thread about running TensorFlow on RPi](https://github.com/tensorflow/tensorflow/issues/254)
* [Parallel thread on building TensorFlow on ARMv7l](https://github.com/tensorflow/tensorflow/issues/445)
	* This is where the most recent conversation is located

## License

Subdirectories contained within the `third_party` directory each contain relevant licenses for the code and software within those subdirectories.

The file TENSORFLOW_LICENSE applies to the binaries distributed in the [releases.](https://github.com/samjabrahams/tensorflow-on-raspberry-pi/releases)

The file LICENSE applies to other files in this repository. I want to stress that a majority of the lines of code found in the guide of this repository was created by others. If any of those original authors want more prominent attribution, please contact me and we can figure out how to make it acceptable.

---

_[Back to top](#installing-tensorflow-on-raspberry-pi-3-and-probably-2-as-well)_
