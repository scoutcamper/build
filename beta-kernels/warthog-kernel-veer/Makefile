NAME = $(shell basename $(shell pwd))
TITLE = WarthogKernel (Veer)
DEVICE = veer
CATEGORY = Beta
VERSIONS = 2.1.1-20 2.1.2-20
APPINFO_DESCRIPTION = In the jungle, the mighty jungle, the lion sleeps tonight. Oh wait... <br><br>\
A collection of all the best kernel improvements for the HP Veer, rolled into a single OTA-safe installation package.<br>\
<b>Note that usage of this package is very likely to <a href=http://developer.palm.com/blog/2010/03/a-statement-on-the-overclocking-patches/>void your warranty</a> if things go wrong.</b><br>\
Current additions include:<ul>\
<li>Support for kernel crypto modules required by TrueCrypt</li>\
<li>Overclock to 1.2GHz</li>\
</ul><br>\
All additions are disabled by default, and must be enabled by using the Govnah application.<br>\
For more information, visit <a href=${HOMEPAGE}>${HOMEPAGE}</a>
DESCRIPTION = ${APPINFO_DESCRIPTION}<br>${KERNEL_DISCLAIMER}
APPINFO_CHANGELOG = [ \
{ "version" : "${WEBOS_VERSION}-20", "log" : [ "OC to 1.2GHz. Boot capped at 1GHz" ] }, \
{ "version" : "${WEBOS_VERSION}-14", "log" : [ "Overclock to 1.018GHz. Undervolt lower speeds. 300HZ clock. Anticipatory IO scheduler" ] }, \
{ "version" : "${WEBOS_VERSION}-8", "log" : [ "Forward port old defconfigs" ] }, \
{ "version" : "${WEBOS_VERSION}-3", "log" : [ "Initial version" ] }, \
]
CHANGELOG = \
${WEBOS_VERSION}-20: OC to 1.2GHz. Boot capped at 1GHz<br>\
${WEBOS_VERSION}-14: Overclock to 1.018GHz. Undervolt lower speeds. 300HZ clock. Anticipatory IO scheduler<br>\
${WEBOS_VERSION}-8: Forward port old defconfigs.<br>\
${WEBOS_VERSION}-3: Initial version.

HOMEPAGE = http://www.webos-internals.org/wiki/Application:WarthogKernel
SRC_GIT = git://git.webos-internals.org/kernels/patches.git
KERNEL_PATCHES = makefiletune/armMakefile.diff \
		 warthogbuild/veer-overclock.patch \
		 warthogbuild/veer-300hz.patch \
		 warthogbuild/defconfig-feat-veer.patch \
		 identification/mkcompile_h.patch \
		 warthogbuild/ident-veer.patch \
		 crypto/truecrypt-support-veer.patch

# 		 defconfig/defconfig-nodebug-veer.patch \
# 		 warthogbuild/defconfig-slim-veer.patch \

# 		 psychobuild/cpu_alignment.patch \
# 		 warthogbuild/defconfig-feat-veer.patch \

TYPE = Kernel

include ../../support/kernel.mk

# Override the compiler
#CROSS_COMPILE_arm = $(shell cd ../.. ; pwd)/toolchain/cs11.03armel/build/arm-2011.03/bin/arm-none-linux-gnueabi-
