

## double-direction-adapter-endless 

powred by rv-adapter-endless   https://github.com/rockerhieu/rv-adapter-endless

双向加载更多 recyclerview, 不同于上拉刷新，下拉加载更多。双向都是加载更多操作

`EndlessRecyclerViewAdapter` support for RecyclerView.Adapter

## feature

* 1，双向加载更多
* 2，支持竖向，和横向
* 3，装饰模式实现，不需要修改之前adapter。

## when use

首次加载中间段数据，然后滚动时，需要加载中间段数据前和后的更多数据，
eg: 乐视视频app（android） 播放页下半屏剧集card的滚动获取

![Renderings](https://github.com/songhanghang/double-direction-adapter-endless/blob/master/screenshots/A0001LRX22Gsonghang03022016174843.gif)

## usage

```java
recyclerView = (RecyclerView) findViewById(R.id.recycler_view);
        LinearLayoutManager layoutManager = new LinearLayoutManager(this);
        layoutManager.setOrientation(LinearLayoutManager.HORIZONTAL);
        recyclerView.setLayoutManager(layoutManager);
        recyclerView.setHasFixedSize(true);
        ArrayList<String> strings = new ArrayList<>();
        adapter = new SimpleStringAdapter(layoutManager, 30, strings);
        endlessRecyclerViewAdapter = new EndlessRecyclerViewAdapter(this, adapter, new EndlessRecyclerViewAdapter.RequestToLoadMoreListener() {
            @Override
            public void onAfterLoadMoreRequested() {
                //load onAfter
            }

            @Override
            public void onBeforeLoadMoreRequested() {
                //load before
            }
        });
        recyclerView.setAdapter(endlessRecyclerViewAdapter);
```

