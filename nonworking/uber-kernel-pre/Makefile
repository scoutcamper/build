NAME = $(shell basename $(shell pwd))
TITLE = UberKernel (Pre/Pre+)
DEVICE = pre
CATEGORY = Experimental
VERSIONS = 1.5.0-113
APPINFO_DESCRIPTION = A collection of all the best kernel improvements for the Palm Pre/Pre+, rolled into a single OTA-safe installation package.<br>\
<b>Note that usage of this package is very likely to <a href=http://developer.palm.com/blog/2010/03/a-statement-on-the-overclocking-patches/>void your warranty</a> if things go wrong.<b><br>\
Current additions include:<ul>\
<li>720MHz, 800MHz and 1GHz kernel operating points, based on the open source OMAP3440 kernel port, ported to the Palm Pre/Pre+ by uNiXpSyChO</li>\
<li>Automatic temperature limiting support, written by uNiXpSyChO, ka6sox & rwhitby</li>\
<li>A new <b>screenstate</b> governor created by uNiXpSyChO specifically for the Palm Pre/Pre+ which runs at a higher speed when the screen is on, and a lower speed when the screen is off</li>\
<li>Modification of the lowmemnotify threshold calculation to take into account free swap space, written by rwhitby</li>\
<li>A new <a href=http://lwn.net/Articles/334649/><b>compcache</b> compressed RAM swap kernel module</a> ported to the Palm Pre/Pre+ by uNiXpSyChO & rwhitby</li>\
<li>The OMAP3430 internal CPU temperature sensor is made available for measuring the true CPU temperature, ported to the Palm Pre/Pre+ by ka6sox & rwhitby</li>\
<li>All standard Linux 2.6.24 <a href=http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/index.html>cpufreq governors</a> made available for selection via the Govnah application</li>\
</ul><br>\
All additions are disabled by default, and must be enabled by using the Govnah application.<br>\
For more information, visit <a href=${HOMEPAGE}>${HOMEPAGE}</a>
DESCRIPTION = ${APPINFO_DESCRIPTION}<br>${KERNEL_DISCLAIMER}
APPINFO_CHANGELOG = [ \
{ "version" : "${WEBOS_VERSION}-113", "log" : [ "Added ability to control core voltages at each frequency", "Added ability to override screenstate charger frequency limiter", "Added a new configurable frequency limiter based on percentage battery remaining", "Reduced 1GHz voltage to save power, based on F105 testing results", "Added USB mass storage patch for XBox360 compatibility" ] }, \
{ "version" : "${WEBOS_VERSION}-92", "log" : [ "Removed 550MHz, added 1GHz" ] }, \
{ "version" : "${WEBOS_VERSION}-87", "log" : [ "Limited frequency to 500MHz when temperature exceeds configurable limits (defaults to 55 degrees)" ] }, \
{ "version" : "${WEBOS_VERSION}-74", "log" : [ "Limited frequency to 500MHz when charging on Touchstone to prevent overheating", "Improved verification of target files for no existing modifications" ] }, \
{ "version" : "${WEBOS_VERSION}-58", "log" : [ "Limited frequency to 500MHz when charging at 1A to prevent overheating" ] }, \
{ "version" : "${WEBOS_VERSION}-50", "log" : [ "Incorporated compile flag performance improvements" ] }, \
{ "version" : "${WEBOS_VERSION}-43", "log" : [ "Updated with latest postinst and prerm OTA safety measures" ] }, \
{ "version" : "${WEBOS_VERSION}-40", "log" : [ "Enabled lower frequencies for screenstate minimum" ] }, \
{ "version" : "${WEBOS_VERSION}-37", "log" : [ "Includes free swap in Too Many Cards memory calculations" ] }, \
{ "version" : "${WEBOS_VERSION}-35", "log" : [ "Added compcache compressed RAM swap kernel module (not loaded by default)" ] }, \
{ "version" : "${WEBOS_VERSION}-32", "log" : [ "Update and cleanup of charging code in screenstate governor" ] }, \
{ "version" : "${WEBOS_VERSION}-21", "log" : [ "Limit IVA2 block to 360MHz as per the mystery bug mentioned in the Palm kernel patch" ] }, \
{ "version" : "${WEBOS_VERSION}-16", "log" : [ "Improved screenstate transition detection" ] }, \
{ "version" : "${WEBOS_VERSION}-13", "log" : [ "Initial public release" ] }, \
]
CHANGELOG = \
${WEBOS_VERSION}-113: Added ability to control core voltages at each frequency. Added ability to override screenstate charger frequency limiter. Added a new configurable frequency limiter based on percentage battery remaining. Reduced 1GHz voltage to save power, based on F105 testing results. Added USB mass storage patch for XBox360 compatibility.<br>\
${WEBOS_VERSION}-92: Removed 550MHz, added 1GHz.<br> \
${WEBOS_VERSION}-87: Limited frequency to 500MHz when temperature exceeds configurable limits (defaults to 55 degrees).<br> \
${WEBOS_VERSION}-74: Limited frequency to 500MHz when charging on Touchstone to prevent overheating. Improved verification of target files for no existing modifications.<br>\
${WEBOS_VERSION}-58: Limited frequency to 500MHz when charging at 1A to prevent overheating.<br>\
${WEBOS_VERSION}-50: Incorporated compile flag performance improvements.<br>\
${WEBOS_VERSION}-43: Updated with latest postinst and prerm OTA safety measures.<br>\
${WEBOS_VERSION}-40: Enabled lower frequencies for screenstate minimum.<br>\
${WEBOS_VERSION}-37: Includes free swap in Too Many Cards memory calculations.<br>\
${WEBOS_VERSION}-35: Added compcache compressed RAM swap kernel module (not loaded by default).<br>\
${WEBOS_VERSION}-32: Update and cleanup of charging code in screenstate governor.<br>\
${WEBOS_VERSION}-21: Limit IVA2 block to 360MHz as per the mystery bug mentioned in the Palm kernel patch.<br>\
${WEBOS_VERSION}-16: Improved screenstate transition detection.<br>\
${WEBOS_VERSION}-13: Initial public release

HOMEPAGE = http://www.webos-internals.org/wiki/Application:UberKernel
SRC_GIT = git://git.webos-internals.org/kernels/patches.git
KERNEL_PATCHES = overclocking/600-720-800-1000-min-opp5.patch overclocking/defconfig-standard.patch \
		 sensors/sensors_temp_omap34xx.patch sensors/defconfig-safe.patch \
		 screenstate/screenstate.patch \
		 makefiletune/armMakefile.diff \
		 defconfig/defconfig.pre.cpugov \
		 compcache/compcache.patch compcache/lowmemnotify-total-memory.patch \
		 overclocking/override.patch overclocking/defconfig-override.patch \
		 usb/f_mass_storage.patch
EXTERNAL_MODULES = compcache/compcache-0.5.4
TYPE = Kernel

include ../../support/kernel.mk

# Override the compiler
CROSS_COMPILE_arm = $(shell cd ../.. ; pwd)/toolchain/cs09q1armel/build/arm-2009q1/bin/arm-none-linux-gnueabi-