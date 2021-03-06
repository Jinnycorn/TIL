# 운영체제


## 운영체제의 개념

### 운영체제(OS; Operating System)

* **컴퓨터 시스템의 자원들을 효율적으로 관리**하며, 사용자가 컴퓨터를 **편리하고 효과적으로 사용할 수 있도록 환경을 제공하는 여러 프로그램의 모임**


### 가상기억장치 구현 기법

* 가상 기억장치
  * **보조기억장치의 일부를 주기억장치처럼 사용하는 것**으로, 용량이 작은 주기억장치를 마치 큰 용량을 가진 것처럼 사용하는 기법
  * 프로그램을 여러 개의 작은 블록단위로 나누어서 가상기억장치에 보관해 놓고, 프로그램 실행 시 요구되는 블록만 주기억장치에 불연속적으로 할당하여 처리

* **일반적인 구현 방법** : 페이징 기법, 세그먼테이션 기법

* 페이징(Paging) 기법
  * 가상기억장치에 보관되어 있는 **프로그램과 주기억장치의 영역을 동일한 크기로 나눈 후** 나눠진 프로그램을 동일하게 나눠진 **주기억장치의 영역에 적재시켜 실행**하는 기법
  * 프로그램을 일정한 크기로 나눈 단위를 페이지(Page)라고 하고, 페이지 크기로 일정하게 나누어진 주기억장치의 단위를 페이지 프레임(Page Frame)이라고 함

* 세그맨테이션(Segmentation) 기법
  * 세그맨테이션 기법은 가상기억장치에 보관되어 있는 **프로그램을 다양한 크기의 논리적인 단위로 나눈 후 주기억장치에 적재시켜 실행**시키는 기법
  * 프로그램을 배열이나 함수 등과 같은 논리적인 크기로 나눈 단위를 세그먼트(Segment)라고 하며, 각 세그먼트는 고유한 이름과 크기를 가짐
  * 세그먼테이션 기법을 이용하는 궁극적 이유는 기억공간 절약을 위함


### 페이지 교체 알고리즘

* 페이지 교체 알고리즘
  * **페이지 부재(Page Fault)가 발생하면** 가상기억장치에서 필요한 페이지를 찾아 주기억장치에 적재해야 하는데, 이때 주기억장치의 모든 페이지 프레임이 사용중이면 **어떤 페이지 프레임을 선택하여 교체할 것인지를 결정**하는 기법
  * *페이지 부재: CPU가 액세스한 가상 페이지가 주기억장치에 없는 경우. 페이지 부재가 발생하면 해당 페이지를 디스크에서 주기억장치로 가져와야 함. 
  * 종류: OPT, FIFO, LRU, LFU, NUR, SCR 등


* OPT(OPTimal replacement, 최적 교체)
  * **앞으로 가장 오랫동안 사용하지 않을 페이지를 교체**하는 기법
  * 페이지 부재 횟수가 가장 적게 발생하는 가장 효율적인 알고리즘

* FIFO(First In First Out)
  * FIFO는 각 페이지가 주기억장치에 적재될 때마다 그때의 시간을 기억시켜 **가장 먼저 들어와서 가장 오래 있었던 페이지를 교체하는** 기법
  * 이해하기 쉽고, 프로그래밍 설계가 간단

* LRU(Least Recently Used)
  * **최근에 가장 오랫동안 사용하지 않은 페이지를 교체** 하는 기법
  * 각 페이지마다 계수기(Counter)나 스택(Stack)을 두어 현시점에서 가장 오랫동안 사용하지 않은, 즉 가장 오래전에 사용된 페이지 교체

* LFU(Least Frequently Used)
  * **사용 빈도가 가장 적은 페이지를 교체**하는 기법
  * 활발하게 사용되는 페이지는 사용 횟수가 많아 교체되지 않고 사용됨

* NUR(Not Used Recently)
  * LRU와 비슷한 알고리즘으로, **최근에 사용하지 않은 페이지를 교체**하는 기법
  * 최근에 사용되지 않은 페이지는 향후에도 사용되지 않을 가능성이 높다는 것을 전제로 LRU에서 나타나는 시간적 오버헤드 줄일 수 있다.
  * 최근 사용 여부 확인 위해 각 페이지마다 두 개의 비트, 즉 참조 비트(Reference Bit)와 변형 비트(Modified Bit, Dirty Bit)가 사용됨

* SCR(Second Chance Replacement, 2차 기회 교체)
  * **가장 오랫동안 주기억장치에 있던 페이지 중 자주 사용되는 페이지의 교체를 방지**하기 위한 기법
  * FIFO 기법의 단점을 보완하는데 사용됨

 
