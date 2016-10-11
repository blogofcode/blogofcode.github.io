---
layout:     post
title:      Image Slideshow using ViewPager with PagerAdapter
date:       2016-10-11 12:31:19
summary:    Perhaps you’ve seen some of the new user interface features available as part of the Android compatibility package. One such feature, image slideshow(horizontal view paging), allows for easy left and right swipes to load different screens (pages), controlled by a single Activity. This feature has been showcased in several high profile applications like the Android Market application and the Google+ Android client.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /image-slideshow-using-viewpager-with-pageadapter/
tags:
  - android
---

In this we are going to make a beautiful image slideshow using viewpager. For that first we need to setup the `MainActivity` in which you want to include the image slideshow.

### Setting Up ViewPager

Firstly, we need to have a `ViewPager` element in our `MainActivity` file located at `res/layout/content_main.xml`

`content_main.xml`:
{% highlight xml %}
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:id="@+id/relativeLayout">


    <android.support.v4.view.ViewPager
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:id="@+id/viewpager"
        android:layout_width="match_parent"
        android:layout_height="150dp">
    </android.support.v4.view.ViewPager>

</RelativeLayout>
{% endhighlight %}

Here I setup height of 150dp, if you want to fill the entire layout, update `android:layout_height="match_parent"` to `android:layout_height="match_parent"`.

### Binding PagerAdapter to ViewPager

Next, in our `onCreate()` Activity method, we'll instantiate our custom `PagerAdapter` implementation and bind it to our `ViewPager` object.

`MainActivity`:
{% highlight java %}
CustomPagerAdapter mCustomPagerAdapter = new CustomPagerAdapter(this, mResources);

ViewPager mViewPager = (ViewPager) findViewById(R.id.viewpager);
mViewPager.setAdapter(mCustomPagerAdapter);
{% endhighlight %}

### Image Drawable Resources

In our Activity, we'll have a images instance variable that'll have an array of drawable resource IDs.

`MainActivity`
{% highlight java %}
int[] mResources = {
        R.drawable.one,
        R.drawable.two,
        R.drawable.three,
        R.drawable.four
};
{% endhighlight %}

Before this, I copied images named`one.jpg`, `two.jpg`, `three.jpg`, `four.jpg` to `res/drawable/`. Then I have these images' resource IDs in mResources array, each one as `R.drawable.` name of image.

### Custom PagerAdapter

Finally, it's time to write our custom pager adapter implementation that'll populate the content pages within our `ViewPager`.

`CustomPagerAdapter`:
{% highlight java %}
class CustomPagerAdapter extends PagerAdapter {
 
    Context mContext;
    LayoutInflater mLayoutInflater;
 
    public CustomPagerAdapter(Context context) {
        mContext = context;
        mLayoutInflater = (LayoutInflater) mContext.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
    }
 
    @Override
    public int getCount() {
        return mResources.length;
    }
 
    @Override
    public boolean isViewFromObject(View view, Object object) {
        return view == ((LinearLayout) object);
    }
 
    @Override
    public Object instantiateItem(ViewGroup container, int position) {
        View itemView = mLayoutInflater.inflate(R.layout.pager_item, container, false);
 
        ImageView imageView = (ImageView) itemView.findViewById(R.id.imageView);
        imageView.setImageResource(mResources[position]);
 
        container.addView(itemView);
 
        return itemView;
    }
 
    @Override
    public void destroyItem(ViewGroup container, int position, Object object) {
        container.removeView((LinearLayout) object);
    }
}
{% endhighlight %}

* `getCount()` - As name suggests, it returns the number of views available, i.e., number of pages to be displayed/created in the `ViewPager`.
* `instantiateItem()` - Here the page is created for the given `position` passed to it as an argument. We `inflate()` our layout resource(`R.layout.pager_item`) and then set resource for the `ImageView` in it. Finally, the inflated view is added to the container, which is the `ViewPager` and return it.
* `destroyItem()` - This method removes the page from container for the given position passed as `position` paramenter. We simply remove `object` using `removeView()` from the container to which we added in the last `instantiateItem()` method. We could also have used `removeViewAt()` by passing `position` as parameter.
* `isViewFromObject()` - Object returned by `instantiateItem()` is a key. This method checks whether the View/Page pssed to it is associated with that key or not. It is required by `PagerAdapter` to function properly. IN our example, we just compare the two instances and return the evaluated boolean.

### Pager Item

Here's how `res/layout/pager_item.xml` will look like which is inflated in the `CustomPagerAdapter` class.

`pager_item.xml`:
{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
 
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
 
    <ImageView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/imageView"
        android:scaleType="fitXY" />
</LinearLayout>
{% endhighlight %}

In this `pager_item.xml`, this is the simplest possible layout we can create. We can also add extra features to the view or the image like adding borders around images or posts(which I will discuss in other poast), adding `layout_margin` in image or post properties and make it beautiful and lookable image slideshow.

Hope you understand.

For those, who don't like to read but just copy the code, here's the [code](https://github.com/johnotander/pixyll).


---
