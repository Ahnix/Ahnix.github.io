---
layout: post
title: "Cloudinary nodejs api"
date: 2021-03-29 15:01:02
image: '/images/cloudinary.png'
description: "Webstorm no console macos."
tags:
- cloudinary
- nodejs
---

<img src="/images/cloudinary.png" style="width: 286px; height: 180px;">


## Instalação

<p> O primeiro passo é instalar as dependecias:</p>
{% highlight zsh %}
npm install express
npm install multer
npm install cloudinary
{% endhighlight %}

<br>

<p> criar o projeto</p>

{% highlight zsh %}

npm init

{% endhighlight %}

<p>criar file de nome index.js com o seguinte conteudo</p>

<script src="https://gist.github.com/Ahnix/2b5c97a3cfbdd0acb9fbcf146aa783b1.js"></script>

<p>O seu package.json deve conter o seguinte conteudo</p>

<script src="https://gist.github.com/Ahnix/f6ca86cae9133bb42475ed22238b150e.js"></script>

<p>basta rodar o npm i em seguida node index.js, sua api de upload estara pronta.
vale ressaltar que no index deve ser preenchido os dados de acesso ao cloudinary.
</p>

