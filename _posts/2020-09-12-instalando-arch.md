---
layout: post
title: "Instalando Arch"
date: 2020-09-12 11:01:02
image: '/images/arch.png'
description: "Instalando Arch linux do zero."
tags:
- Arch
- jekyll
- linux
---

<img src="/images/arch.png" style="width: 286px; height: 180px;">

## Download
<p> Você encontra a ISOs para download do Arch Linux <a href="https://www.archlinux.org/download/"> Clique Aqui!</a></p>
<p> Depois é só usar um pen drive bootável da distro.</p>


## Instalação

<p> O primeiro passo é ajustar o seu teclado</p>
{% highlight bash %}
loadkeys br-abnt2
{% endhighlight %}

<p>Toda a instalação do Arch precisa de acesso à internet, por isso é importante que você esteja conectado.</p>
{% highlight bash %}
ping 1.1.1.1
{% endhighlight %}

<p>Caso você tenha Wi-Fi:</p>
{% highlight bash %}
wifi-menu
{% endhighlight %}

<p>O próximo passo é conferir as suas partições</p>
{% highlight bash %}
fdisk -l /dev/sda
{% endhighlight %}

<p>Defina suas partições conforme seu hd ou seu gosto.</p>
<p>No meu caso ficou:</p>

{% highlight bash %}
/dev/sda1 (500MB para o /boot/efi)
/dev/sda2 (todo o resto para o /)
{% endhighlight %}

<p>O GRUB no meu caso a /dev/sda1/ type EFI BIOS . O próximo passo é formatá-las:</p>
{% highlight bash %}
mkfs.fat -F32 /dev/sda1
{% endhighlight %}
{% highlight bash %}
mkfs.ext4 /dev/sda2
{% endhighlight %}

## Pontos de montagem
{% highlight bash %}
mount /dev/sda2 /mnt
{% endhighlight %}
{% highlight bash %}
mkdir /mnt/boot/efi
{% endhighlight %}

## Instalação dos pacotes base do Arch
{% highlight bash %}
pacstrap /mnt base base-devel linux linux-firmware
{% endhighlight %}


## Vamos gerar a nossa tabela FSTAB
{% highlight bash %}
genfstab -U -p /mnt >> /mnt/etc/fstab
{% endhighlight %}

## Chroot
{% highlight bash %}
arch-chroot /mnt
{% endhighlight %}

## Definindo Horário
{% highlight bash %}
ln -sf /usr/share/zoneinfo/America/Bahia /etc/localtime
{% endhighlight %}

## Definindo variável de linguagem
{% highlight bash %}
echo LANG=pt_BR.UTF-8 >> /etc/locale.conf
{% endhighlight %}

## Definindo teclado abnt2
{% highlight bash %}
echo KEYMAP=br-abnt2 >> /etc/vconsole.conf
{% endhighlight %}

## Definindo host
{% highlight bash %}
echo "arch" >> /etc/hosts
{% endhighlight %}
{% highlight bash %}
echo "127.0.0.1      localhost.localdomain            localhost" >> /etc/hosts
{% endhighlight %}

## senha root
{% highlight bash %}
passwd
{% endhighlight %}

## criando user

<p>Troque o archuser pelo seu nome de usuario</p>

{% highlight bash %}
useradd -m -g users -G wheel archuser
{% endhighlight %}

## Instalar pacotes uteis
{% highlight bash %}
pacman -S dosfstools os-prober mtools network-manager-applet networkmanager wpa_supplicant wireless_tools dialog sudo dhclient wget vim nano screen  
{% endhighlight %}

## Sudoers
<p>Troque o archuser pelo seu nome de usuario</p>
{% highlight bash %}
archuser ALL=(ALL) ALL
{% endhighlight %}

## EFIboot
{% highlight bash %}
pacman -S grub-efi-x86_64 efibootmgr
{% endhighlight %}
{% highlight bash %}
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=arch_grub --recheck
{% endhighlight %}
{% highlight bash %}
cp /usr/share/locale/en@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo
{% endhighlight %}
{% highlight bash %}
grub-mkconfig -o /boot/grub/grub.cfg
{% endhighlight %}

## Instalação concluida
<p>Agora basta efetuar um crtl+d e reboot</p>
