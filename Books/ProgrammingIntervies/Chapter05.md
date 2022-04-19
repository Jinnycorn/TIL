# Chapter05. 연결 리스트

**본 내용은 프로그래밍 면접 이렇게 준비한다를 토대로 작성하였습니다.**



### 연결 리스트의 종류
* 단일 연결 리스트(면접 문제), 이중 연결 리스트, 원형 연결 리스트
* 단일 연결 리스트
  
```C
//단일 연결 리스트 원소
typedef struct IntElement{
  struct IntElement *next;
  int data;
}IntElement;

```
