# resizeVolume

# /dev/nvme0n1 - volume name, 1 - partition index
sudo growpart /dev/nvme0n1 1 
# block for xfs
# / - mount from above. Command will safely fail for non xfs
sudo xfs_growfs -d / 
# block for ext4
# /dev/nvme0n1p1 - partition you would like to extend
sudo resize2fs /dev/nvme0n1p1
