# resizeVolume
We can increase the volume size with the new EBS Feature Elastic volumes, post that we need to follow the following steps to use the increase size as shown here

Assume your volume was 16G and you increased it to 32GB.

    $lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  32G  0 disk
└─xvda1 202:1    0  16G  0 part /

To extend xvda1 from 16GB t0 32GB, we need growpart. growpart is available as part of cloudutils

sudo apt install cloud-utils

Post installation of cloud-utils, execute the growpart command

sudo growpart /dev/xvda 1

Now lsblk, will show

    $ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0  32G  0 disk
└─xvda1 202:1    0  32G  0 part /

but df -h will show only 16GB

Final command for extending xvda1 to 32GB is

sudo resize2fs /dev/xvda1

In case of XFS file system,

sudo xfs_growfs /dev/xvdal
