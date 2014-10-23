---
layout: post
title: android的ListView常见问题
description: android的ListView常见问题
category: blog
---
### android listView addHeaderView的问题
	隐藏headerView的思路:使用View.GONE属性隐藏
{% highlight java linenos %}
<LinearLayout android:id="@+id/item_root"
    android:layout_width="fill_parent"
    android:layout_height="50dip"
    android:orientation="vertical" >
<TextView  android:id="@+id/tv_1" />
<TextView  android:id="@+id/tv_2" />
</LinearLayout >
{% endhighlight %}
	此时，有如下逻辑：
{% highlight java linenos %}
ListView listView = xxxx;
  listView.addHearderView(item_root);
  listView.setAdapter(adapter);
  adapter.add(xxxxx);添加数据
  item_root.setVisibility(View.GONE);
{% endhighlight %}
	实测发现使用View.GONE方法后，头部依然会占用相应的高度无法隐藏。
	原因是：如果直接修改根布局的属性，就会造成headerView的显示有问题。
	所以修改成操作item_root里头的View显示就好了。
	
### 添加HeaderView之后尺寸布局被忽略
	通常添加头部的方法是 
{% highlight java linenos %}
LayoutInflater lif = (LayoutInflater) getSystemService(Context.LAYOUT_INFLATER_SERVICE);
View headerView = lif.inflate(R.layout.header, null);
mListView.addHeaderView(headerView);
{% endhighlight %}
原因：
lif.inflate(R.layout.header, null)丢失了XML布局中根View的LayoutParam，应该使用的是 
{% highlight java linenos %}
lif.inflate(R.layout.header, mListView, false);
{% endhighlight %}


### 添加HeaderView之后导致OnItemClickListener的position移位
OnItemClickListener接口的方法：
{% highlight java linenos %}
void onItemClick(AdapterView<?> parent, View view, int position, long id)
{% endhighlight %}
position通常是从0开始的，但是添加了HeaderView之后，position也会将HeaderView的数目计算进去。 
几个解决办法： 
1.手动计算真实的position位置： 
{% highlight java linenos %}
final headerCount = 1;
mListView.setOnItemClickListener(new OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, View view,
            int position, long id) {
        Item item = myAdapter.getItem(position - headerCount);
    }
});
{% endhighlight %}

2.其实上面的步骤ListView已经为我们提供了，所以可以改写为：
{% highlight java linenos %}
mListView.setOnItemClickListener(new OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, View view,
            int position, long id) {
        Item item = parent.getAdapter().getItem(position);
    }
});

{% endhighlight %}
原因在源码中有比较清晰的解释： 
当有headerView被添加时，实际传递给ListView的adapter被包装，parent.getAdapter()返回真实被ListView使用的Adapter（HeaderViewListAdapter），HeaderViewListAdapter的getItem(int)方法处理了position的问题。 
[yangming]:  

