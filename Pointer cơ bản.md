# Pointer cơ bản

- Con trỏ được đĩnh nghĩa có thể lưu trữ đĩa chỉ của các biến hoặc vị trí trong bộ nhớ. Ta có thể truy cập thao tác dữ liệu trên vùng nhớ đấy bằng con trỏ
- Khi con trữ lưu trữ địa chỉ vùng nhớ, kích thước của nó không phụ thuộc vào dữ liệu mà chúng trỏ tới. Nó chỉ phụ thuộc vào kiến trúc của hệ thống. **32bit - 4 byte, 64bit - 8 byte**

## Syntax:

```c
datatype * ptr;
```

```c
int *iPtr; // con trỏ đến 1 địa chỉ chứa giá trị số nguyên
double *dPtr; // con trỏ đến 1 địa chỉ chứa giá trị số thực
int *iPtr4, *iPtr5; // khai báo 2 con trỏ đến các biến số nguyên

int* funtionex();
```

- Ptr : tên con trỏ
- kiểu dữ liệu của con trỏ

Sử dụng con trỏ:

1. khai báo con trỏ:

```c
int *ptr;
```

1. Gán giá trị cho con trỏ:

```c
int var = 10;
int * ptr;
ptr = &var;
```

Chúng ta cũng có thể khai báo và khởi tạo con trỏ chỉ trong một bước. Phương thức này được gọi là định nghĩa con trỏ vì con trỏ được khai báo và khởi tạo cùng một lúc:

```c
int *ptr = &var;
```

3. Truy cập vào vùng nhớ mà con trỏ trỏ đến;

```c
#include <stdio.h>

int main()
{
    int value = 10;
    printf("%p\n", &value); // in địa chỉ biến value
    printf("%d\n", value); // in giá trị biến value

    int *ptr = &value; // ptr trỏ đến biến value
    printf("%p\n", ptr); // in địa chỉ con trỏ ptr trỏ đến, tương đương &value
    printf("%d\n", *ptr); // in giá trị tại địa chỉ mà ptr trỏ đến, tương đương value

    return 0;
}
```

Sau khi được gán, giá trị con trỏ có thể được gán lại cho một giá trị khác:

```c
#include <stdio.h>

int main()
{
    int value1 = 5;
    int value2 = 7;

    int *ptr;

    ptr = &value1; // ptr trỏ đến value1
    printf("%d\n", *ptr); // in ra giá trị của value1, kết quả là 5

    ptr = &value2; // ptr giờ trỏ đến value2
    printf("%d\n", *ptr); // in ra giá trị của value2, kết quả là 7

    return 0;
}
```

**Chú ý:** Khi địa chỉ của **biến value** được gán cho **con trỏ ptr**:

- **ptr** tương đương với **&value**
- **ptr** được xử lý giống như **value**

Vì ***ptr** được xử lý giống như **value**, nên ta có thể gán giá trị cho ***ptr** như 1 biến thông thường:

```c
value = 5;
int *ptr = &value; // ptr points to value

	*ptr = 7; // *ptr tương đương với value
```

## Con trỏ trong Array:

```c
#include <stdio.h>

int main()
{
    int arr[5] = {1, 2, 3, 4, 5};
    int *ptr = arr; // ptr trỏ đến địa chỉ của phần tử đầu tiên trong mảng

    // In các phần tử của mảng bằng cách sử dụng con trỏ
    for (int i = 0; i < 5; i++)
    {
        printf("%d ", *ptr); // In giá trị của phần tử mà con trỏ đang trỏ đến
        ptr++; // Di chuyển con trỏ để trỏ đến phần tử tiếp theo trong mảng
    }

    return 0;
}
```

```c
1 2 3 4 5
```

Trong ví dụ trên, con trỏ **`ptr`** trỏ đến địa chỉ của phần tử đầu tiên trong mảng **`arr`**. Sau đó, chúng ta sử dụng con trỏ **`ptr`** để truy cập các phần tử trong mảng bằng cách dùng **`*ptr`**. Tiếp theo, chúng ta di chuyển con trỏ **`ptr`** để nó trỏ đến các phần tử tiếp theo trong mảng bằng cách thay đổi giá trị của nó **`ptr++`**.

⇒ Điều này là do địa chỉ của các phần tử trong mảng liên tiếp nhau và các kiểu dữ liệu nguyên (int) có kích thước cố định.

 Ta xét mảng **`int arr[5] = {1, 2, 3, 4, 5};`**. Mảng này bao gồm 5 phần tử kiểu int. Khi chúng ta khai báo con trỏ **`int *ptr = arr;`**, con trỏ sẽ trỏ đến địa chỉ của phần tử đầu tiên trong mảng, tức là **`arr[0]`**. Khi thực hiện **`ptr++`**, con trỏ sẽ di chuyển đến địa chỉ của phần tử tiếp theo, tức là **`arr[1]`**. Tiếp tục thực hiện **`ptr++`**, con trỏ sẽ trỏ đến **`arr[2]`**, và cứ tiếp tục như vậy cho đến khi hết mảng.

**khi truyền một mảng cho một hàm, mảng sẽ được chuyển đổi ngầm định thành một con trỏ trỏ đến mảng, và con trỏ được truyền vào hàm:**