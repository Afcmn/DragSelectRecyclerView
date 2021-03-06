###DragSelectRecyclerView [![Release](https://jitpack.io/v/MFlisar/DragSelectRecyclerView.svg)](https://jitpack.io/#MFlisar/DragSelectRecyclerView) [![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-DragSelectRecyclerView-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/5152)

### What is it / What does it do?
It's a simple one class `TouchListener` that can be attached to any RecyclerView and handles multi selection in google photos style via long pressing on an item and moving the finger up/down to select more items (it even scrolls if you reach the edges of the `RecyclerView`)

![Demo](https://github.com/MFlisar/DragSelectRecyclerView/blob/master/files/demo.gif?raw=true)
 
### Gradle (via [JitPack.io](https://jitpack.io/))

1. add jitpack to your project's `build.gradle`:

	```groovy
	repositories {
	    maven { url "https://jitpack.io" }
	}
	```
2. add the compile statement to your module's `build.gradle`:

	```groovy
	dependencies {
	    compile 'com.github.MFlisar:DragSelectRecyclerView:0.2'
	}
	```

### Usage

1. Create the a touch listener like following

	```
	mDragSelectTouchListener = new DragSelectTouchListener()
		.withSelectListener(new DragSelectTouchListener.OnDragSelectListener() {
			@Override
			public void onSelectChange(int start, int end, boolean isSelected) {
				// update your selection
				// range is inclusive start/end positions
			}
		})
		// following is all optional
		.withMaxScrollDistance(distance)    // default: 16; 	defines the speed of the auto scrolling
		.withTopOffset(toolbarHeight)       // default: 0; 		set an offset for the touch region on top of the RecyclerView
		.withBottomOffset(toolbarHeight)    // default: 0; 		set an offset for the touch region on bottom of the RecyclerView
		.withScrollAboveTopRegion(enabled)  // default: true; 	enable auto scrolling, even if the finger is moved above the top region
		.withScrollBelowTopRegion(enabled)  // default: true; 	enable auto scrolling, even if the finger is moved below the top region
		.withDebug(enabled);                // default: false;
	```

2. attach it to the `RecyclerView`

	```
	recyclerView.addOnItemTouchListener(mDragSelectTouchListener);
	```

3. on item long press, inform the listener so that it can start doing it's magic

	```
	// if one item is long pressed, we start the drag selection like following:
	// we just call this function and pass in the position of the first selected item
	mDragSelectTouchListener.startDragSelection(position);
	```
	
###TODO

* support horizontal RecyclerViews... should be quite simple, but is not yet implemented
	
###Credits

This library is heavily inspired and based on https://github.com/weidongjian/AndroidDragSelect-SimulateGooglePhoto
