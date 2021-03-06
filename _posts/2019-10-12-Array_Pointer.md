---
layout: page
title: Pointer & Array
categories: [C language]
tags: [C language]

---


# Pointer & Array

嘗試了幾個範例，做點紀錄。

一維陣列傳遞
```C
// 一維陣列傳遞
void display_array(int arr[], int size)
{
    for(int i = 0; i < size; i++)
    {
        printf("%d \n",arr[i]);
    }
}

void display_array(int *arr, int size)
{
    for(int i = 0; i < size; i++)
    {
        printf("%d \n", *(arr+i) );
    }
}

int main()
{
    int arr[5] = {1,2,3,4,5};
    display_array(arr,5);
    
}

```

二維陣列傳遞
```C

void display_array(int (*arr)[5], int size)
{
    for(int i = 0; i < 2; i++)
    {
        for(int j = 0;j < size;j++)
        {
            printf("%d \n", arr[i][j]);
        }
        
    }
}

void display_matrix(int arr[][5], int size)
{
    for(int i = 0; i < 2; i++)
    {
        for(int j = 0;j < size;j++)
        {
            printf("%d \n", arr[i][j]);
        }
        
    }
}

int main()
{
    int matrix[2][5] = 
    {
        {1,2,3,4,5},
        {6,7,8,9,10}
    };
    display_matrix(matrix,5);
    
    // 另外一種寫法
    int (*p_matrix)[5] = matrix;
    /* 宣告一個指向陣列的pointer p_matrix。
     * p_matrix定義為一個指向二維陣列的pointer，每列有5個元素
     * 所以 p_matrix[0] 指到記憶體位置為 matrix[0][0]的位置
     * p_matrix[1] 指到記憶體位置為 matrix[1][0]的位置
    */
    
    display_matrix(p_matrix,5);
    
    /* 如果是宣告成 int *p_matrix[5];
     * 則代表 一個 p_matrix的陣列，長度為5，陣列裡面裝的是 指向 integer的pointer
     *
    */
}

```



```C

void display_matrix(int **arr,int size)
{
    for(int i = 0; i < 2; i++)
    {
        for(int j = 0;j < size;j++)
        {
            printf("%d \n", arr[i][j]);
        }
        
    }
}

int main()
{
    int (*(matrix_t[])) = 
    {
       (int[]) {1,2,3,4,5},
       (int[]) {6,7,8,9,10}
    };
    
    
    display_matrix(matrix_t,5);
    
    // 另外一種寫法
    /* 宣告一個陣列 matrix_t，裝指向integer的 pointer
     * matrix_t[0] : 指向 陣列 {1,2,3,4,5}的pointer
     * matrix_t[1] : 指向 陣列 {6,7,8,9,10}的pointer     
     * 所以傳給funtion是 pointer 的 pointer
    */

}

```
