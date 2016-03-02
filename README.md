

## double-direction-adapter-endless 

powred by rv-adapter-endless

`EndlessRecyclerViewAdapter` support for RecyclerView.Adapter

## Usage

To use `EndlessRecyclerViewAdapter` you need to create a subclass that will control the endlessness, specifying what `View` to use for the loading placeholder.

When the loading view is shown, it will send a request to load more data via the interface `RequestToLoadMoreListener`. After loading the data, you can let the adapter know via `onDataReady()` method.

```java
OriginalAdapter adapter = new OriginalAdapter();
EndlessRecyclerViewAdapter endlessRecyclerViewAdapter = new EndlessRecyclerViewAdapter(this, adapter, new RequestToLoadMoreListener() {
   @Override
   public void onLoadMoreRequested() {
      loadMoreData(new OnSuccess() {
        void onSuccess(List<Item> items) {
          adapter.append(items);
          // notify that the data is ready, and the adapter SHOULD continue to load more
          endlessRecyclerViewAdapter.onDataReady(true);
        }
      }, new OnError() {
        void onError() {
          // notify that the data is ready, and the adapter SHOULD NOT continue to load more
          endlessRecyclerViewAdapter.onDataReady(false);
        }
      )
   }
});
rv.setAdapter(endlessRecyclerViewAdapter);
```

You can have a look at the example project for more details.
