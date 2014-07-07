migrando do django 1.4 para 1.5


Buenas! Recentemente atualizei uma aplicação "gorda" para a versão 1.5.5 do Django e resolvi compartilhar essa experiência.
Foi um pouco demorado, mas nada realmente que dure mais de um dia de trabalho. Primeiramente leia a [release notes](https://docs.djangoproject.com/en/dev/releases/1.5/ "release notes django 1.5"), não precisei ler nenhum outro 
artigo além desse para migrar minha aplicação.

#### Third apps ####

Pacotes como o ```simplejson``` e ```localflavor``` foram removidos do Django e agora são apps terceiras. A simplejson pode ser facilmente substituída pelo módulo [json](http://docs.python.org/2.7/library/json.html#module-json "json") nativo da linguagem.
Enquanto a localflavor é atualizado assim.




#### new-style url ####
url from future

exemplos

#### deprecate warnings ####
exemplos como djangorestframework, django-tinymce


#### Django 1.6 ####

Eu sei, eu sei. Nesse fim de ano saiu a primeira release estável da 1.6, talvez vocês se perguntem porquê eu não fiz o upgrade da 1.4.x para 1.6.0 e as respostas são simples.
Baby-steps, seria traumático demais fazer essa atualização sem resolver as coisas novas da 1.5 primeiro e o outro porém, dependências. Muitas libs ainda estão fazendo esse trabalho
de upgrade, grande parte possue o Django 1.5.x como sua versão estável. Mas nada problemático, logo logo também faremos esse trabalho e posto aqui novamente. ;)


Meu ambiente de trabalho em 7 itens

1 - Unix

