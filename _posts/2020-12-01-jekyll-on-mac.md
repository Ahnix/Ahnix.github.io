---
layout: post
title: "Instalando  Jekyll on mac."
date: 2020-12-01 11:01:02
image: '/images/skell/jekyll.png'
description: "Instalando  Jekyll on mac."
tags:
- macbook
- jekyll
- mac
---

<img src="/images/skell/jekyll.png" style="width: 286px; height: 180px;">


## Instalação

<p> O primeiro passo é instalar o brew e o ruby</p>
{% highlight bash %}
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install ruby
{% endhighlight %}

<p>Adicione o path do ruby a sua shell</p>
{% highlight bash %}
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc
{% endhighlight %}

<p>instalando o jekyll e bundler</p>
{% highlight bash %}
gem install --user-install bundler jekyll
{% endhighlight %}

<p>criando seu primeiro site</p>
{% highlight bash %}
jekyll new myblog
{% endhighlight %}


<p>Rodando o servidor</p>
{% highlight bash %}
bundle exec jekyll serve
{% endhighlight %}

## Processo concluído 
