---
layout: post
title:  "Redimensionando imagens no Android"
date:   2019-08-09
---

<p class="intro"><span class="dropcap">O</span> Android disponibiliza muitas opções para o ajuste e redimensionamento de imagens através do componente ImageView.</p>

Uma ImageView pode ser ajustada por meio da propriedade scaleType com os atributos: CENTER, CENTER_CROP, CENTER_INSIDE,  FIT_CENTER, FIT_END, FIT_START, FIT_XY, MATRIX.

O objetivo deste post é apresentar um pequeno projeto no qual é possível enviar uma imagem e visualizar os resultados de redimensionamento para cada um dos atributos.

# Imagem apresentada nos diferentes tipos de escala:

<img src="{{ '/assets/img/imageScaled.gif' | prepend: site.baseurl }}" alt="" style="margin:0 auto; display:block;"> 

O projeto de exemplo pode ser baixado do Github: <a href="https://github.com/lidiomar/android-image-scale-type" target="blank">https://github.com/lidiomar/android-image-scale-type</a>