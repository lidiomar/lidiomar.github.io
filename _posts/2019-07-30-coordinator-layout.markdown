---
layout: post
title:  "CoordinatorLayout"
date:   2019-07-30
---

<p class="intro"><span class="dropcap">N</span>a Google I/O 2015 foi feito o lançamento de um nova support library que contém ViewGroups como AppbarLayout, CollapsingToolbarLayout e CoordinatorLayout.</p>

ActionBar é o componente visual utilizado por padrão em aplicações android, porém recomenda-se a utilização da Toolbar na implementação da AppBar devido a sua flexibilidade e facilidade de customização.

CoordinatorLayout por sua vez é o componente responsável por realizar muitos dos efeitos de scroll definidos no material design, atualmente existem diversas formas de utiliza-lo juntamente com a app bar. 
O objetivo desse post é mostrar alguns exemplos de utilização destes componentes, bem como a exploração de algumas de suas propriedades.

# Expandindo e contraindo a Toolbar:

<img src="{{ '/assets/img/coordinator.gif' | prepend: site.baseurl }}" alt="" style="margin:0 auto; display:block;"> 

CoordinatorLayout, juntamente com CollapsingToolbarLayout é frequentemente utilizado para dar o efeito de esconder e mostrar a AppBar. O código abaixo apresenta a implementação desse comportamento:


{% highlight xml %}
<android.support.design.widget.CoordinatorLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".MainActivity">

    <android.support.design.widget.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <android.support.design.widget.CollapsingToolbarLayout
            android:id="@+id/collapsingToolbar"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            app:titleEnabled="false"
            app:layout_scrollFlags="scroll|enterAlways|enterAlwaysCollapsed">

            <android.support.v7.widget.Toolbar
                android:id="@+id/toolbar"
                app:titleEnabled="true"
                app:layout_scrollFlags="scroll|enterAlways"
                android:layout_width="match_parent"
                android:layout_height="?attr/actionBarSize"
                app:title="Coordinator Test"
                android:minHeight="?attr/actionBarSize"/>

        </android.support.design.widget.CollapsingToolbarLayout>

    </android.support.design.widget.AppBarLayout>

    <android.support.v4.widget.NestedScrollView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:layout_behavior="@string/appbar_scrolling_view_behavior">

        <LinearLayout
            android:orientation="vertical"
            android:layout_width="match_parent"
            android:layout_height="wrap_content">

            <TextView
                android:layout_height="60dp"
                android:gravity="center_vertical"
                android:layout_width="wrap_content"
                android:text="AAAAAAA"/>
        </LinearLayout>
    </android.support.v4.widget.NestedScrollView>
</android.support.design.widget.CoordinatorLayout>
{% endhighlight %}