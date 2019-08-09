---
layout: post
title:  "CoordinatorLayout"
date:   2019-07-30
---

<p class="intro"><span class="dropcap">I</span>n the 2015 Google I/O  was released the new support library that contains ViewGroups like AppBarLayout, CollapsingToolbarLayout and CoordinatorLayout.</p>

ActionBar is the default visual component used in Android applications, however the adoption of the AppBar component is recommended due your flexibility and easy customization.

On the other hand, CoordinatorLayout is the component responsible to acomplishing many of the scroll effects defined on
material design guidelines. Nowadays there are many ways of your utilization with the App bar. The purpose of this post is to show some examples of using these components, as well as exploring some of their properties.

# Toolbar: Expanding and Shrinking

<img src="{{ '/assets/img/coordinator.gif' | prepend: site.baseurl }}" alt="" style="margin:0 auto; display:block;"> 

CoordinatorLayout, along with CollapsingToolbarLayout is often used to give AppBar the hide and show effect. The code
below presents the implementation of this behavior:

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