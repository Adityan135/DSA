# MinHeap Implementation step-by-step

## 1. Define MinHeap, initialize and print

As a first step, we define an array based MinHeap, a constructor that takes an array passed as argument to initialize the heap and a print method that outputs the contents of the heap.

``` java
// MinHeap.java

public class MinHeap {
    int[] arr;

    public MinHeap(int[] keys) {
        arr = keys;  // Make arr point to keys array
    }

    public void print()  {
        for (int i=0; i<arr.length; i++)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```

``` java
MinHeapInitTest.java

public class MinHeapInitTest {

    public static void main(String[] args) {
        int[] keys = {5, 3, 8, 6, 2, 1, 7, 9, 4, 0};
        MinHeap m = new MinHeap(keys);
        m.print();
    }
}
```

## 2. Add methods to get parent, left child and right children

## 3. Add method to swap elements at given indices

## 4. Add method to check if swap is required

## 5. Add method to fix heap underneath a node

## 6. Add method to build heap
