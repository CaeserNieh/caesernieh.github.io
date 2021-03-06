---
layout: page
title: Funtion Pointer
categories: [C language]
tags: [C language]

---


# Function Pointer


顧名思義，一個指向Function的Pointer。

用法1 : 
```C
#include <stdio.h>

int add(int a, int b){
    return a+b;
}

int main()
{
    // a pointer(func_ptr) point to function with parameter m,n
    int (*func_ptr)(int m, int n);
    func_ptr = add;
    printf("func_ptr(3,5) : %d\n",func_ptr(3,5));
    return 0;
}

```

用法2 typedef : 
```C
#include <stdio.h>

typedef int(*Func_ptr)(int a, int b);

int add(int a, int b){
    return a+b;
}

int main()
{
    Func_ptr f_ptr = add;
    printf("func_ptr(3,5) : %d\n",f_ptr(3,5));
    return 0;
}

```


> (* (void( * )( ) )0 )();

Jserv的不能不知道的C語言裡提到的，該如何解讀呢? 
根據Jserv的YT教學，上面的程式碼可變成
> typedef void(* funct_ptr)();
> (* (funct_ptr) 0)()

先define一個function pointer(funct_ptr) point to funcion return void
再透過這個function pointer(funct_ptr)去指 address 0x0。在value of pointer 去執行這項Function
以這個例子來說，會core_dump。
以下範例佐證。
``` C
#include <stdio.h>

typedef int(*OP)();

typedef int(*func)();

int aa(){
    return 0xAA;
}

int main(){
    OP f_ptr = aa;
    
    //  EX : address aa : 0x40052d
    printf("address of func aa : %p\n",aa);
    
    // *f_ptr = f_ptr = 0x40052d
    printf("value of func_ptr f_ptr : %p\n",f_ptr);
    
    // return 0xAA 
    printf("(*f_ptr) () : %d\n", (*f_ptr)());
    
    // return 0xAA 
    printf("(* ((func)0x40052d) )() : %d\n", (* ((func)0x40052d) )());
    
    
    return 0
}
    
```

以上範例使用function pointer func 指向 aa()的address並且執行，因此之後對 func dereference，同意於直接執行aa()。

回到正題，上面用funct_ptr指向 address 0x0，並且執行。因為0x0不是一個能隨意執行存取的記憶體位置，因此會core dump



---

> http://ccckmit.wikidot.com/cp:function
> http://computer-learning-note.blogspot.com/2013/08/pointer-to-functionaka-function-pointer.html
> https://blog.xuite.net/jesonchung/scienceview/93554949-typedef+%E4%B8%8D%E5%90%8C%E7%9A%84%E7%94%A8%E6%B3%95
