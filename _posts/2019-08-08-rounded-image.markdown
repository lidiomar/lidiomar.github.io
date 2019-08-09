---
layout: post
title:  "Imagens arredondadas no Android"
date:   2019-08-08
---

<p class="intro"><span class="dropcap">A</span> utilização de imagens com bordas arredondas é comumente utilizada em aplicativos Android, podendo ser destacados por exemplo a exibição da imagem de perfil de quem está comentando um post, uma tela de dados de usuário dentre outros.</p>

Esse post foi criado com a intenção de apresentar um app Android onde é possível enviar uma imagem e apresenta-la redimensionada, arredondada e com uma fina borda ao redor.

### Redimensionando a imagem:

{% highlight kotlin %}
    val centerCropBitmap = ThumbnailUtils.extractThumbnail(bitmap, 150, 150)
{% endhighlight %}

### Deixando a imagem arredondada:

{% highlight kotlin %}
    val roundedBitmap = RoundedBitmapDrawableFactory.create(resources, centerCropBitmap)
            roundedBitmap.isCircular = true
            roundedBitmap.isFilterBitmap = true
            roundedBitmap.setAntiAlias(true)
{% endhighlight %}

### Arquivo circle.xml, será utilizado como background da imagem:
{% highlight xml %}
    <shape xmlns:android="http://schemas.android.com/apk/res/android"
        android:shape="oval">
        <stroke android:width="1dp" android:color="@color/colorPrimary"/>
    </shape>
{% endhighlight %}


### Layout da tela:
{% highlight xml %}
    <LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:orientation="vertical"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center_horizontal"
        tools:context=".MainActivity">

        <Button
            android:id="@+id/button"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="15dp"
            android:layout_marginBottom="15dp"
            android:text="Get Image" />

        <ImageView
            android:id="@+id/original"
            android:visibility="gone"
            android:layout_width="150dp"
            android:layout_height="150dp"
            android:background="@drawable/circle"
            android:padding="1dp"
            android:cropToPadding="true"
            android:layout_marginBottom="15dp" />

    </LinearLayout>
{% endhighlight %}


O projeto de exemplo pode ser baixado do Github: <a href="https://github.com/lidiomar/android-rounded-image" target="blank">https://github.com/lidiomar/android-rounded-image</a>