## Comparator for string in lexicographical order :

```cpp
bool cmp(string x,string y) 
{
	return x+y<y+x;
}
```


## Sample Uses:
## Sorting An Array In Reverse Order
<br>
``Method 1:``

```cpp
vector a;
sort(a.rbegin(), a.rend());
```

<br>

``Method 2:``

```cpp
//For an vector
bool cmp(int a,int b) {
    return a <= b;
}

int main() {
    int n;
    cin >> n;

    vector a;

    for (int i = 0; i < n; i++) {
        int x;
        cin >> x;
        a.push_back(x);
    }

    sort (a.begin(), a.end(), cmp);

    for (int i = 0; i < a.size(); i++)
        cout << a[i] << " ";
    
    return 0;
}
```
## For an array now.

<br>

```cpp
bool cmp(int a,int b) {
    return a <= b;
}

int a[100];

int main() {
    int n;
    cin &>> n;

    for (int i = 0; i < n; i++) {
       cin >> a[i];
    }

    sort (a, a + n, cmp);

    for (int i = 0; i < a.size(); i++)
        cout << a[i] << " ";

    return 0;
}
```

<br>

# The End
