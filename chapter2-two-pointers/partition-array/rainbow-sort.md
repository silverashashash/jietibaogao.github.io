## Rainbow sort

* 不用counting sort，可能达到的最佳时间复杂度？排除O\(n\*k\)，因为如果k=n，会退化成n^2，这样就不如用quicksort。O\(nlogn\) 也排除，因为肯定跟k有关。当k=1时为O\(1\)；k=2为O\(n\)，即partition；k=3为O\(n\) ，partition两次。k=n时为O\(nlogn\)，这样推算时间复杂度为O\(nlogk\)，根据这个目标想算法。
* rainbow sort综合了merge sort和quick sort的思想

![](/assets/Screen Shot 2019-08-22 at 4.14.41 PM.png)



