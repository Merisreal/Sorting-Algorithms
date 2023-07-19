# Cấu trúc dữ liệu và giải thuật

# Selectionsort

Chọn ra một phần tử lớn nhất hoặc nhỏ nhất đặt nó vào vị trí đầu tiên. Sau đó tiếp tục chọn phần tử nhỏ nhất của mảng đặt vào vị trí thích hợp, lặp lại cho đến khi hết mảng

Độ phức tạp: O(n^2)

### A. Ưu điểm:

- dể hiểu, dễ triễn khai, phù hợp cho các bài toán nhỏ, trường hợp đơn giản

### B. Nhược điểm

- Độ phức tạp thời gian lớn: Selection Sort có độ phức tạp thời gian O(n^2), tức là nếu có n phần tử trong danh sách, thì số lần so sánh và hoán đổi sẽ là O(n^2). Điều này làm cho thuật toán chậm hơn trong các trường hợp có số lượng phần tử lớn.

### C.Cách hoạt động:

First Pass:

- Mảng [5,2,1,8,9]
- Chọn MinIndex là phẩn tử đầu tiên, duyệt mảng từ 0-4 tìm được 1 là phần tử nhỏ nhất mảng
- Hoán đổi 5 với 1 ⇒ [1,2,5,9,8]

Second pass:

- Vị trí hiện tại là [2]
- Minindex = 2, duyệt mảng từ 1-4 tìm được 2 là phần tử nhỏ nhất nên không thay đổi
- ⇒ [1,2,5,8,9]

⇒ lặp lại đến khi hoàn chỉnh mảng ta được [1,2,5,8,9]

```cpp
#include <stdio.h>
#include <string.h>

void swap(int *xp, int *yp)
{
    int temp = *xp;
    *xp = *yp;
    *yp = temp;
}

void Slection_sort(int array[],int len)
{
    int j,i,minIndex;
    
     for (i = 0; i < len - 1; i++)
    {
        minIndex = i;
        
        for (j = i + 1; j < len; j++)
        {
            if (array[j] < array[minIndex])
                minIndex = j;
        }

        if (minIndex != i)
        {
            swap(&array[minIndex], &array[i]);
        }
}

}
void Print_Array(int array[],int len)
{
    for (int i =0;i<len;i++)
    {
        printf("%d ", array[i]);
    }
}

int main()
{
    
    int array[] ={512,4111,23,12,21};
    int len=sizeof(array)/sizeof(array[0]);
    Slection_sort(array ,len);
    Print_Array(array,len);
}
```

# Bubblesort

So sánh 2 cặp phần tử liền kề, phần tử lớn nhất sẽ được đẩy về bên phải

Độ phức tặp: O(n^2)

### A. Ưu điểm

- Dễ nhận biết danh sách đã sắp xếp: Sau mỗi lần hoán đổi, Bubble Sort đưa phần tử lớn nhất (hoặc nhỏ nhất) trong danh sách lên đầu. Do đó, ta có thể dễ dàng nhận biết khi danh sách đã được sắp xếp hoàn chỉnh.
- Dễ hiểu và triển khai:

### B. Nhược điểm

- Độ phức tạp thời gian lớn: Selection Sort có độ phức tạp thời gian O(n^2), tức là nếu có n phần tử trong danh sách, thì số lần so sánh và hoán đổi sẽ là O(n^2). Điều này làm cho thuật toán chậm hơn trong các trường hợp có số lượng phần tử lớn.

### C. Cách hoạt động:

So sánh các cặp phần tử liền kề nhau, bắt đầu đi từ đầu danh sách, 2 phần tử đang so sánh phần tử bên phải nhỏ hơn phần tử bên trái, ta hoán đổi chúng 

Di chuyển phần tử nhỏ nhất lên đầu: Sau khi hoán đổi, phần tử nhỏ nhất trong đoạn đã xét sẽ được đưa lên đầu danh sách. Điều này đảm bảo rằng phần tử nhỏ nhất đã đúng vị trí và không bị hoán đổi tiếp trong các lần duyệt sau.

```cpp
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

void swap(int *xp, int *yp)
{
    int temp = *xp;
    *xp = *yp;
    *yp = temp;
}

void Bubble_Sort(int array[],int len)
{
    int j,i;
    bool mustswap;
    for (i = 0; i < len - 1; i++)
    {
        mustswap = false;
        for (j = 0; j < len-i-1; j++)
        {
            if (array[j] > array[j+1])
            {   
                swap(&array[j], &array[j+1]);
                mustswap = true;
            }
        }
        if (mustswap = false)
        {
            break;
        }
    }

}
void Print_Array(int array[],int len)
{
    for (int i =0;i<len;i++)
    {
        printf("%d ", array[i]);
    }
}

int main()
{
    int array[] ={512,4111,23,12,21};
    int len=sizeof(array)/sizeof(array[0]);
    Bubble_Sort(array ,len);
    Print_Array(array,len);
}
```

# **Insertion Sort**

Bắt đầu từ phần tử thứ i = 1; nếu nhỏ hơn phần tử i = 0;  phần tử thứ 0 sẽ cộng thêm 1 nhường chỗ cho phần tử thứ i +1;

Độ phức tạp: O(n^2)

### A.Ưu điểm

- Insertion Sort có hiệu suất tốt hơn trong việc sắp xếp danh sách gần sắp xếp. Khi danh sách đã gần sắp xếp, số lần so sánh và dịch chuyển phần tử sẽ ít hơn so với danh sách không được sắp xếp hoặc ngẫu nhiên.

### B. Nhược điểm

- Độ phức tạp thời gian lớn: Selection Sort có độ phức tạp thời gian O(n^2), tức là nếu có n phần tử trong danh sách, thì số lần so sánh và hoán đổi sẽ là O(n^2). Điều này làm cho thuật toán chậm hơn trong các trường hợp có số lượng phần tử lớn.

### C. Cách hoạt động

Bắt đầu từ phần tử thứ hai, thuật toán duyệt qua các phần tử chưa sắp xếp một cách tuần tự.

sau đó chèn phần tử vào vị trí đúng: Đối với mỗi phần tử chưa sắp xếp, thuật toán so sánh nó với các phần tử trong phần đã sắp xếp. Nếu phần tử chưa sắp xếp nhỏ hơn phần tử trong phần đã sắp xếp, ta dịch chuyển phần tử trong phần đã sắp xếp sang phải để tạo chỗ cho phần tử chưa sắp xếp, và chèn phần tử đó vào vị trí đúng.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1b87f9d-f931-483f-af43-f4c84455ca70/Untitled.png)

```cpp
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

void Insertion_sort(int array[],int len)
{
    int j,i,key,pos;
    for (i = 1; i < len ; i++)
    {   
        key = array[i];
        pos = i-1;
        while (pos >= 0 && key < array[pos])
        {
            array[pos + 1] = array[pos];
            --pos;
        }
        array[pos+1] = key;
    }

}
void Print_Array(int array[],int len)
{
    for (int i =0;i<len;i++)
    {
        printf("%d ", array[i]);
    }
}

int main()
{
    int array[] ={512,4111,23,12,21};
    int len=sizeof(array)/sizeof(array[0]);
    Insertion_sort(array ,len);
    Print_Array(array,len);
}
```

# QuickSort

Quick sort là một thuật toán chia để trị( Divide and Conquer algorithm). Nó chọn một phần tử trong mảng làm điểm đánh dấu(pivot). Thuật toán sẽ thực hiện chia mảng thành các mảng con dựa vào pivot đã chọn. Việc lựa chọn pivot ảnh hưởng rất nhiều tới tốc độ sắp xếp. Nhưng máy tính lại không thể biết khi nào thì nên chọn theo cách nào. Dưới đây là một số cách để chọn pivot thường được sử dụng:

1. Luôn chọn phần tử đầu tiên của mảng.
2. Luôn chọn phần tử cuối cùng của mảng. (Được sử dụng trong bài viết này)
3. Chọn một phần tử random.
4. Chọn một phần tử có giá trị nằm giữa mảng(median element).

### A. Ưu điểm:

Hiệu suất cao: QuickSort là một trong những thuật toán sắp xếp nhanh nhất trong số các thuật toán so sánh. Trung bình, độ phức tạp thời gian của QuickSort là O(n log n), với n là kích thước mảng đầu vào. Trong các trường hợp tốt nhất, độ phức tạp có thể là O(n log n), khi mảng được phân hoạch đều.

### B. Nhược điểm:

Độ phức tạp tệ nhất có thể là O(n^2): Trong trường hợp xấu nhất, khi phần tử chốt được chọn không tạo ra phân hoạch cân đối, QuickSort có thể chạy với độ phức tạp là O(n^2), với n là kích thước mảng. Điều này xảy ra khi mảng đã sắp xếp hoặc gần như sắp xếp. Tuy nhiên, với cải tiến như chọn ngẫu nhiên phần tử chốt hoặc sử dụng phương pháp phân hoạch tối ưu, khả năng xảy ra trường hợp xấu nhất có thể giảm đi.

Không ổn định: QuickSort không đảm bảo tính ổn định trong việc sắp xếp. Điều này có nghĩa là hai phần tử bằng nhau có thể bị đảo chỗ trong quá trình sắp xếp, dẫn đến sự thay đổi vị trí tương đối giữa các phần tử có cùng giá trị.

### C. Cách hoạt động:

```cpp
#include<stdio.h>
#include<string.h>

void quicksort(int array[],int first,int last){
    int i, j, pivot, temp;
    if(first<last){
        pivot=first;
        i=first;
        j=last;
        while(i<j){
            while(array[i]<=array[pivot]&&i<last)
            i++;
            while(array[j]>array[pivot])
            j--;
            if(i<j){
                temp=array[i];
                array[i]=array[j];
                array[j]=temp;
            }
        }
        temp=array[pivot];
        array[pivot]=array[j];
        array[j]=temp;
        quicksort(array,first,j-1);
        quicksort(array,j+1,last);
    }
}
int main(){
    int i, count, array[]={5,4,3,2,1};
    int len = sizeof(array)/sizeof(array[0]);
    quicksort(array,0,len);
    for(i=0;i<len;i++)
    printf(" %d",array[i]);
    return 0;
}
```

https://www.tutorialspoint.com/explain-the-quick-sort-technique-in-c-language