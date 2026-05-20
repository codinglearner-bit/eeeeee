#code 
[inverse] codes=
#include <iostream>
#include <vector>

using namespace std;

void printArray(vector<int>& arr) {
    for (int x : arr) {
        cout << x << " ";
    }
    cout << endl;
}

void bounceSort(vector<int>& arr) {
    bool swapped = true;
    int start = 0;
    int end = arr.size() - 1;

    while (swapped) {
        swapped = false;

        // Move bigger numbers right
        for (int i = start; i < end; i++) {
            if (arr[i] > arr[i + 1]) {
                swap(arr[i], arr[i + 1]);
                swapped = true;
            }
        }

        if (!swapped)
            break;

        swapped = false;
        end--;

        // Move smaller numbers left
        for (int i = end - 1; i >= start; i--) {
            if (arr[i] > arr[i + 1]) {
                swap(arr[i], arr[i + 1]);
                swapped = true;
            }
        }

        start++;

        printArray(arr);
    }
}

int main() {
    vector<int> numbers = {9, 3, 7, 1, 5, 2, 8};

    cout << "Original Array:\n";
    printArray(numbers);

    cout << "\nSorting...\n";
    bounceSort(numbers);

    cout << "\nSorted Array:\n";
    printArray(numbers);

    return 0;
}
