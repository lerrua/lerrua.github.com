---
layout: post
title: "Migrando sua app Django da 1.4 para 1.5"
date: 2013-12-18 12:35
comments: true
categories: [django]
---
<!--more-->


Buenas! Recentemente atualizei uma aplicação "gorda" para a versão 1.5.5 do Django e resolvi compartilhar essa experiência.
Foi um pouco demorado, mas nada realmente que dure mais de um dia de trabalho. Primeiramente leia a [release notes](https://docs.djangoproject.com/en/dev/releases/1.5/ "release notes django 1.5"), não precisei ler nenhum outro 
artigo além desse para migrar minha aplicação.

#### Third apps ####

Módulos como o ```simplejson``` e ```localflavor``` foram removidos do Django e se tornaram apps independentes. A simplejson pode ser facilmente substituída pelo módulo [json](http://docs.python.org/2.7/library/json.html#module-json "json") nativo da linguagem.

Outros módulos também serão deprecados nas próximas releases, então para não ter tanto trabalho futuro sugiro dar uma lida na [deprecation timeline](https://docs.djangoproject.com/en/dev/internals/deprecation/ "roadmap") e já se preparar para eventuais mudanças.


#### New-style url ####
O padrão de urls nas templates mudou, use: 
```html
{% raw %}{% url "app:my_view" param1 %}{% endraw %}
``` 
ao invés de:
```{% raw %}{% url app:my_view param1 %}{% endraw %}```.

Esse "novo" padrão é válido desde a 1.3, desde que esteja usando a ```load url from future``` em seu template.


#### Deprecate warnings ####
É normal a primeiro momento rodar um runserver e se deparar com vários warnings no terminal, alguns warnings de deprecations que você solucionou os mantenedores de suas libs terceiras também terão de solucionar. Recomendo fortemente visitar
as docs de suas principais dependências e verificar o changelog, provavelmente algum homem de bem criou uma versão especifica compatível com a versão de Django que você usa. 

Tendo esse cuidado acredito que esses warnings sumirão e você terá menos trabalho para um futuro upgrade em sua aplicação.


#### Django 1.6 ####

Nesse fim de ano saiu a primeira release estável da 1.6, talvez vocês se perguntem porquê eu não fiz o upgrade da 1.4.x diretamente para 1.6.0 e as respostas são simples.

Baby-steps, seria traumático demais fazer essa atualização sem resolver as coisas novas da 1.5 primeiro e um outro motivo, dependências. Muitas libs ainda estão fazendo esse trabalho
de upgrade, onde grande parte ainda tem o Django 1.5 como base de sua release estável. Mas nada problemático, logo logo também farei esse trabalho e posto aqui novamente. ;)
