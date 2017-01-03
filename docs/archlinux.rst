Arch Linux
===========

U盘安装
---------

磁盘分区::

    lsblk
    parted
    (parted) mklabel gpt
    (parted) mkpart ESP fat32 1MiB 513MiB
    (parted) set 1 boot on
    (parted) mkpart primary ext4 513MiB 100%

挂载磁盘::

    mount /dev/sdxy /mnt
    mkdir -p /mnt/boot
    mount /dev/sdxz /mnt/boot

磁盘格式化::

    mkfs.fat -F32 /dev/sdxy
    mkfs.ext4 /dev/sdxy
    mkswap /dev/sdxy
    swapon /dev/sdxy

安装基础包::

    vi /etc/pacman.d/mirrorlist
    pacstrap -i /mnt base base-devel

生成配置文件::

    genfstab -U /mnt >> /mnt/etc/fstab

切换到archlinux::

    arch-chroot /mnt /bin/bash

本地化::

    locale-gen
    vi /etc/locale.gen
    tzselect

安装Boot Loader::

    bootctl install

设置主机名称::
    
    vi /etc/hostname

设置密码::
    
    passwd

重启::

    umount -R /mnt
    reboot


基础配置
---------

添加用户/组::

    groupadd chen
    useradd -m -g chen chen
    passwd chen
    vim /etc/sudoers

安装桌面环境::

    pacman -S xorg-xinit
    pacman -S xfce4

安装字体::

    pacman -S ttf-bitstream-vera
    pacman -S adobe-source-code-pro-fonts
    pacman -S wqy-zenhei

安装输入法::

    pacman -S fcitx
    pacman -S fcitx-sunpinyin
    pacman -S fcitx-gtk2
    pacman -S fcitx-configtool

使用VPN::

    pacman -S pptpclient

登录windows系统::

    sudo pacman -S rdesktop
    rdesktop -g 1440x900 -P -z -x l -r sound:off 192.168.1.1

使用Samba::

    sudo pacman -S samba
    cd /etc/samba/
    sudo cp smb.conf.default smb.conf

    vim smb.conf
