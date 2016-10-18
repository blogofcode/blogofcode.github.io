---
layout:     post
title:      Custom Horizontal ListView Using RecyclerView
date:       2016-10-18 12:31:19
summary:    HorizontalListView is an Android ListView widget which scrolls horizontally. Android Studio only provides Vertical ListView widget. Here I have derived customized HorizontalListview widget by extending RecyclerView Adapter.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /custom-horizontal-listview-using-recyclerview/
tags:
  - android-tag
---

<!-- ![desk](https://github.com/blogofcode/blogofcode.github.io/blob/master/images/image-slideshow-using-viewpager-with-pageadapter/image_slideshow1.gif?raw=true) -->

In this we are going to create horizontal listview using `RecyclerView`. For that first we need to setup the `MainActivity` in which you want to include the horizontal listview.

### Setting Up RecyclerView

Firstly, we need to have a `RecyclerView` element in our `MainActivity` file located at `res/layout/content_main.xml`

`content_main.xml`:
{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/content_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <android.support.v7.widget.RecyclerView
        android:id="@+id/horizontal_list"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

</RelativeLayout>
{% endhighlight %}

Here I setup height as `wrap_content`, if you want to fill the entire layout, update `android:layout_height="wrap_content"` to `android:layout_height="match_parent"`.

### Binding RecyclerView to Adapter

Next, in our `onCreate()` Activity method, we'll instantiate our custom `RecyclerView` implementation and bind it to our `RecyclerView.Adapter` object.

`MainActivity`:
{% highlight java %}
List<String> data;
// data to display

RecyclerView horizontalListView = (RecyclerView) findViewById(R.id.horizontal_list);
horizontalListView.setLayoutManager(new LinearLayoutManager(this, LinearLayoutManager.HORIZONTAL, false));

HorizontalAdapter horizontalAdapter = new HorizontalAdapter();
horizontalAdapter.setData(dataList, this);
horizontalListView.setAdapter(horizontalAdapter);
{% endhighlight %}

In this, we get `RecyclerView` with id `horizontal_list` and set it's layout by `.setLayoutManager` method to horizontal `LinearLayoutManager.HORIZONTAL`.
We then create new `HorizontalAdapter` and pass data(`dataList`) and context(`this`) as input parameters.
At last, we set `horizontalAdapter` to `horizontalListView`.

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

### Implement RecyclerView.Adapter

It's time to write our custom `RecyclerView.Adapter` implementation that'll display the content within our `RecyclerView`.

`CustomPagerAdapter`:
{% highlight java %}
class HorizontalAdapter extends RecyclerView.Adapter<RecyclerView.ViewHolder> {

    private List<String> dataList;
    Context cont;

    public HorizontalAdapter() {
    }

    public void setData(List<String> data, Context cont) {
        if (dataList != data) {
            dataList = data;
            this.cont = cont;
            notifyDataSetChanged();
        }
    }

    private class ItemViewHolder extends RecyclerView.ViewHolder {

        private ImageView image;

        public ItemViewHolder(View itemView) {
            super(itemView);
            image = (ImageView) itemView.findViewById(R.id.image);
        }
    }

    @Override
    public RecyclerView.ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        Context context = parent.getContext();
        View itemView = LayoutInflater.from(context).inflate(R.layout.horizontal_list_item, parent, false);
        ItemViewHolder holder = new ItemViewHolder(itemView);
        return holder;
    }

    @Override
    public void onBindViewHolder(RecyclerView.ViewHolder rawHolder, int position) {
        ItemViewHolder holder = (ItemViewHolder) rawHolder;
        String str = dataList.get(position);
        holder.imageView.setImageResource(dataList.get(position));
    }

    @Override
    public int getItemCount() {
        return dataList.size();
    }
}
{% endhighlight %}

### Horizontal List Item

Here's how `res/layout/horizontal_list_item.xml` will look like which is inflated in the `HorizontalAdapter` class.

`horizontal_list_item.xml`:
{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
 
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="wrap_content">
 
    <ImageView
        android:layout_width="match_parent"
        android:layout_height="150dp"
        android:id="@+id/image"
        android:scaleType="fitXY" />
</LinearLayout>
{% endhighlight %}

You can change `horizontal_list_item.xml` to your need and update it in `HorizontalAdapter` in both `ItemViewHolder` and `onBindViewHolder` methods.

Hope this creates horizontal listview with images scrolling easily.

<!-- For those, who don't like to read but just copy the code, here's the [code](https://github.com/johnotander/pixyll). -->


---
