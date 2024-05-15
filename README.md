#include <iostream>

using namespace std;

void NhapMang(int a[], int n)
{
    int i = 0;
    while (i < n)
    {
        std::cout << "Nhập giá trị phần tử thứ " << i + 1 << ": ";
        std::cin >> a[i];
        i++;
    }
}

int ViTriSoLonNhat(int a[], int n, int p)
{
    if (p >= n)
    {
        std::cout << "Error out of index" << std::endl;
        return -1;
    }
    int maxIndex = p;
    for (int i = p + 1; i < n; ++i)
    {
        if (a[i] > a[maxIndex])
        {
            maxIndex = i;
        }
    }
    return maxIndex;
}

void printArray(int arr[], int n)
{
    for (int i = 0; i < n; ++i)
    {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

void Swap(int &a, int &b)
{
    int temp = a;
    a = b;
    b = temp;
}

void SelectionSort(int arr[], int n)
{
    for (int i = 0; i < n - 1; ++i)
    {
        int maxIndex = ViTriSoLonNhat(arr, n, i);
        Swap(arr[maxIndex], arr[i]);
    }
}

int KiemTraGiamDan(int arr[], int n)
{
    int i = 0;
    while (i < n - 1)
    {
        if (arr[i] < arr[i + 1])
            return 0;
        else
            i++;
    }
    return 1;
}

int main()
{
    int n;
    do
    {
        std::cout << "Nhập số lượng phần tử của mảng (tối thiểu 2, tối đa 100): ";
        std::cin >> n;
        if (n <= 2 || n > 100)
        {
            std::cout << "Dữ liệu không hợp lệ, xin mời thử lại" << std::endl;
        }
    } while (n <= 2 || n > 100);

    int arr[n];
    NhapMang(arr, n);

    int isDecrease = KiemTraGiamDan(arr, n);
    if (isDecrease == 1)
    {
        std::cout << "Mảng nhập vào đã được sắp sếp GIẢM DẦN" << std::endl;
        return 1;
    }
    SelectionSort(arr, n);
    std::cout << "Mảng sau khi sắp sếp GIẢM DẦN: ";
    printArray(arr, n);
    return 1;
}
