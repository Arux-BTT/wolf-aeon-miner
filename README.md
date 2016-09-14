# wolf-aeon-miner
Wolf's OpenCL AEON Miner for AMD GPUs

If you get an error about clCreateBuffer - lower your rawintensity. See the example config aeon.conf for details.

Generally, you want to raise rawintensity as high as it will go without error - but remember, 1MiB of GPU RAM is needed for every work-item.

The GPU fan, powertune, and clock setting options are accepted, as the configuration routine was ripped from my own full-custom miner, but they do nothing.

Requires OpenCL 2 headers (AMD APP SDK 3.0 has them), and GCC greater than 4.9 (I used 5.2.)

.... hyc's additions (Linux only):

Use a GPU index of -1 to run on the CPU. The only other config item needed is "threads",
but rawIntensity and worksize must still be set to a non-zero value.

As with the original CPU miner, you can gain a performance boost by configuring huge pages.
Check current setting with "sysctl vm.nr_hugepages" then set it to at least 3 times the
total number of threads you're using, as root.
	sudo sysctl -w vm.nr_hugepages=num

Also, it can run faster as root, which allows it to use mlock.
