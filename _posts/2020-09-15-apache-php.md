---
layout: post
title: "Apache PHP"
date: 2020-09-15 11:01:02
image: '/images/apache-php.png'
description: "Apache PHP"
tags:
- Apache
- Php
- Arch
- Linux
---

<img src="/images/apache-php.png" style="width: 286px; height: 180px;">



<p> Instalando docker e containers do postgresql "psql". </p>

## Instalando Apache

{% highlight bash %}
sudo pacman -S apache
{% endhighlight %}

{% highlight bash %}
sudo systemctl start httpd.service
{% endhighlight %}

{% highlight bash %}
sudo systemctl enable httpd.service
{% endhighlight %}

<p>Para testarmos nossa instalação do Apache, abra seu navegador, e acesse: http://localhost/ </p>

## Instalando php

{% highlight bash %}
sudo pacman -S php php-apache
{% endhighlight %}

<p> Vamos editar o arquivo httpd.conf desta forma: </p>

{% highlight bash %}
sudo vim /etc/httpd/conf/httpd.conf
{% endhighlight %}

<p>Comente esta linha, colocando um # no início da linha, ficando desta forma:</p>
{% highlight bash %}
#LoadModule mpm_event_module modules/mod_mpm_event.so
{% endhighlight %}
<p>Descomente esta linha, retirando # no início da linha, ficando desta forma:</p>
{% highlight bash %}
LoadModule mpm_prefork_module modules/mod_mpm_prefork.so
LoadModule rewrite_module          modules/mod_rewrite.so
{% endhighlight %}

{% highlight bash %}
LoadModule dir_module modules/mod_dir.so
{% endhighlight %}
<p>Logo abaixo desta linha, insira a linha abaixo:</p>
{% highlight bash %}
LoadModule php7_module modules/libphp7.so
{% endhighlight %}

<p>Agora, procure a seção onde temos uma série de Include, e insira no final desta parte a linha abaixo:</p>
{% highlight bash %}
Include conf/extra/php7_module.conf
{% endhighlight %}

<p>Salve o arquivo, e reinicie o Apache, para podermos testar se o PHP está funcionando corretamente.</p>
{% highlight bash %}
sudo systemctl restart httpd.service
{% endhighlight %}
