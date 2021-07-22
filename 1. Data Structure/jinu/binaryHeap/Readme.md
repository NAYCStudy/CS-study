```
public class MaxHeap {
    int Capacity;
    int Size;
    int[] Elements;

    public MaxHeap(int maximumSize) {
        Capacity = maximumSize;
        Elements = new int[maximumSize + 1];
        Size = 0;
        // Elements[0] is sentinel
        Elements[0] = Integer.MAX_VALUE;
    }

    public boolean isFull() {
        return Size == Capacity;
    }

    public boolean isEmpty() {
        return Size == 0;
    }

    public void insert(int value) {
        int i;

        if (isFull())
            throw new ArrayStoreException();

        for (i = ++Size; Elements[i / 2] < value; i /= 2)
            Elements[i] = Elements[i / 2];

        Elements[i] = value;
    }

    public int findMax() {
        if (Size == 0)
            throw new ArithmeticException();

        return Elements[1];
    }

    public int deleteMax() {
        int max, last;
        int i, child;

        if (isEmpty())
            throw new ArithmeticException();

        max = Elements[1];
        last = Elements[Size--];

        for (i = 1; i * 2 <= Size; i = child) {
            // Find smaller child.
            child = i * 2;
            if (child != Size && Elements[child + 1] > Elements[child])
                child++;

            if (last < Elements[child])
                Elements[i] = Elements[child];
            else
                break;
        }

        Elements[i] = last;

        return max;
    }
}
```
