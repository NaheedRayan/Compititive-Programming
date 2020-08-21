## Merging two sorted arrays with O(1) extra space

```
#include <iostream>
#include <algorithm>
using namespace std;

// Utility function to print contents of an array
void printArray(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        cout << arr[i] << " ";
    }

    cout << '\n';
}

// in-place merge two sorted arrays X[] and Y[]
// invariant: X[] and Y[] are sorted at any point
void merge(int X[], int Y[], int m, int n)
{
    // consider each element X[i] of array X and ignore the element
    // if it is already in correct order else swap it with next smaller
    // element which happens to be first element of Y
    for (int i = 0; i < m; i++)
    {
        // compare current element of X[] with first element of Y[]
        if (X[i] > Y[0])
        {
            swap(X[i], Y[0]);
            int first = Y[0];

            // move Y[0] to its correct position to maintain sorted
            // order of Y[]. Note: Y[1..n-1] is already sorted
            int k;
            for (k = 1; k < n && Y[k] < first; k++)
            {
                Y[k - 1] = Y[k];
            }

            Y[k - 1] = first;
        }
    }
}

int main()
{
    int X[] = {1, 4, 7, 8, 10};
    int Y[] = {2, 3, 9};

    int m = sizeof(X) / sizeof(X[0]);
    int n = sizeof(Y) / sizeof(Y[0]);

    merge(X, Y, m, n);

    cout << "X: ";
    printArray(X, m);
    cout << "Y: ";
    printArray(Y, n);

    return 0;
}


```

## Efficiently merging two sorted arrays with O(1) extra space

```
// Merging two sorted arrays with O(1)
// extra space
#include <bits/stdc++.h>
using namespace std;

// Function to find next gap.
int nextGap(int gap)
{
    if (gap <= 1)
        return 0;
    return (gap / 2) + (gap % 2);
}

void merge(int arr1[], int arr2[], int n, int m)
{
    int i, j, gap = n + m;
    for (gap = nextGap(gap); gap > 0; gap = nextGap(gap))
    {
        // comparing elements in the first array.
        for (i = 0; i + gap < n; i++)
            if (arr1[i] > arr1[i + gap])
                swap(arr1[i], arr1[i + gap]);

        //comparing elements in both arrays.
        for (j = gap > n ? gap - n : 0; i < n && j < m; i++, j++)
            if (arr1[i] > arr2[j])
                swap(arr1[i], arr2[j]);

        if (j < m)
        {
            //comparing elements in the second array.
            for (j = 0; j + gap < m; j++)
                if (arr2[j] > arr2[j + gap])
                    swap(arr2[j], arr2[j + gap]);
        }
    }
}

// Driver code
int main()
{
    int a1[] = {10, 27, 38, 43, 82};
    int a2[] = {3, 9};
    int n = sizeof(a1) / sizeof(int);
    int m = sizeof(a2) / sizeof(int);

    merge(a1, a2, n, m);

    printf("First Array: ");
    for (int i = 0; i < n; i++)
        printf("%d ", a1[i]);

    printf("\nSecond Array: ");
    for (int i = 0; i < m; i++)
        printf("%d ", a2[i]);
    printf("\n");
    return 0;
}
```