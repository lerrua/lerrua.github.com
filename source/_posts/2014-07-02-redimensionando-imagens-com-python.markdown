---
layout: post
title: "Redimensionando imagens com Python"
date: 2014-07-02 21:18
comments: true
categories: python
---
<!--more-->

Nós programadores perdemos um tempo tentando mexer em programas de edição de imagem como Photoshop e Gimp para 
quebrar algum galho, tarefas bobas como redimensionar uma imagem para um determinado tamanho sem perder a qualidade por exemplo.

Perda de tempo maior ainda seria se fossem 20 ou 30 imagens, imaginem? Pois é.

Sorte que com python podemos automatizar esse trabalho com apenas algumas linhas de código.

```
pip install Pillow 
```

Pillow é um fork mantido pela comunidade da PIL (Python Image Library), é com ela que vamos fazer essa brincadeira.

```python
import PIL

# Queremos gerar uma imagem com tamanho 300x200
wsize = 300
hsize = 200

img = PIL.Image.open('/path/to/original_picture.png')

# redimensionamos sem perder a qualidade
img = img.resize((wsize, hsize), PIL.Image.ANTIALIAS)
img.save('/path/to/new_img.png')
```

Pronto! Sua `new_img.png` foi gerada na pasta que apontou acima.

Quanto ao problema que citei no começo desse post, é uma solução bastante simples. Vamos apenas iterar esse código acima, mais ou menos assim:

```python
# Vamos supor que esses são os nomes das imagens
IMGS = [
    'original_img_1',
    'original_img_2',
    'original_img_3',
    'original_img_4',
]

for i in IMGS:
    wsize = 300
    hsize = 200
    img = PIL.Image.open('/path/to/{}.png'.format(i))
    img = img.resize((wsize, hsize), PIL.Image.ANTIALIAS)
    # na pasta /thumbs será gerada a imagem com mesmo 
    # nome que a imagem original.
    img.save('/path/to/thumbs/{}.png'.format(i))
```

E é isso, se pensarmos em número de 20 imagens então acabamos de economizar um precioso tempo que seria gasto com um trabalho bem chato e repetitivo.
