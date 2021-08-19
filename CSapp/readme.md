# 小端字节排序

```c
#include <stdio.h>

typedef unsigned char *byte_pointer; // 将数据类型 byte_pointer 定义为一个指向类型为“unsigned char”的对象的指针

void show_bytes(byte_pointer start, size_t len){
    size_t i;
    for(i=0;i<len;i++)
        printf("%.2x",start[i]);
    printf("\n");
}

void show_int(int x){
    show_bytes((byte_pointer) &x, sizeof(int));
    printf("sizeof: %ld \n",sizeof(int));
}

void show_float(float x){
    show_bytes((byte_pointer)&x,sizeof(float));
    printf("sizeof: %ld \n",sizeof(float));

}

void show_pointer(void *x){
    show_bytes((byte_pointer)&x,sizeof(void *));
    printf("sizeof: %ld \n",sizeof(void *));

}

int main() {
    printf("Hello, Worldwf!\n");
    int x = 10;
    byte_pointer *p = (byte_pointer *) 's';
    float f=1.22;
    show_int(x);    //0a000000 sizeof:4
    show_float(f);  // f6289c3f 4
    show_pointer(p); //7300000000000000 8
    return 0;
}
```

