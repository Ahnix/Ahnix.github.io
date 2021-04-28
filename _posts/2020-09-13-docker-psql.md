---
layout: post
title: "Docker Psql"
date: 2020-09-13 11:01:02
image: '/images/dockpsql.png'
description: "Instalando docker psql"
tags:
- Docker
- Psql
- Jekyll
- Linux
---

<img src="/images/dockpsql.png" style="width: 286px; height: 180px;">

<p> Instalando docker e containers do postgresql "psql". </p>

## Obtendo as imagens necessárias

{% highlight bash %}
docker pull dpage/pgadmin4
{% endhighlight %}

{% highlight bash %}
docker pull postgres
{% endhighlight %}


## Criando rede bridge para o postgres rodar

{% highlight bash %}
docker network create --driver bridge postgres-network
{% endhighlight %}

## Obtendo as imagens necessárias

{% highlight bash %}
docker run --name postgres --network=postgres-network -e "POSTGRES_PASSWORD=suasenha" -p 5432:5432 -v ~/PostgreSQL:/var/lib/postgresql/data -d postgres
{% endhighlight %}

{% highlight bash %}
docker run --name pgadmin --network=postgres-network -p 15432:80 -e "PGADMIN_DEFAULT_EMAIL=ramon@gmail.com" -e "PGADMIN_DEFAULT_PASSWORD=suasenha" -d dpage/pgadmin4
{% endhighlight %}


## Acesso PGADMIN

{% highlight bash %}
http://localhost:15432
{% endhighlight %}


## Acesso console
{% highlight bash %}
ifconfig docker0
{% endhighlight %}

<p>Colete o ip e efetue Acesso.</p>

{% highlight bash %}
psql -U postgres -h "ip coletado"
{% endhighlight %}


## Screenshots
![pgadmin](/images/pgadmin.png)
![pgadmin](/images/pgadmin1.png)
