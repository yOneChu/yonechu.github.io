---
layout: post
title:  "운영체제 개요"
date:   2019-05-21
author: YoungHwan Kim
categories: OS
comment : true
tags:	운영체제 OpeartingSystem OS
cover:  ""
---

## 운영체제 개념 및  정의 ##
* 하드웨어와 사용자 및 다른 소프트웨어를 연결해 주는 것
* 우리가 컴퓨터를 사용할 때 운영체제가 없으면 컴퓨터는 깡통에 불과하며, 이 깡통을 최소한 동작시켜주기 위해서 필요한 소프트웨어가 운영체제 이다
* 운영체제도 하나의 소프트웨어 이기 때문에 컴퓨터의 전원이 켜지면 동시에 메모리에 올라가야 동작한다.
* 그런데 운영체제는 너무 크기 때문에, 꼭 필요한 핵심적인 부분만 컴퓨터 전원이 켜질때 메모리에 올려놓고, 이외 의 부분은 필요할 때마다 메모리에 올려놓고 사용한다. 이때, 핵심적인 부분을 '커널(Kernel)'이라고 한다.

---
## 운영체제의 자원관리 기능 ##
* 운영체제의 자원관리 기능은 운영체제의 핵심 기능이다.
* 자원은 하드웨어, 소프트웨어 자원으로 나눌수 있다.
* 하드웨어 자원으로는 CPU, 메모리, 주변장치 및 입출력 장치 등이 있다.

---
## CPU 관리 ##
* 일반적인 컴퓨터에는 CPU가 하나밖에 없지만 프로세스는 여러개가 동시에 실행 됨.
   매 시점 어떤 프로세스에 CPU를 할당해 작업을 처리할 것인지 결정해야 되는데 이것을 CPU 스케줄링(CPU 
   Scheduling) 이라고 한다.
* 스케줄링 기법
**1) 선입선출**
먼저 도착한 프로세스를 CPU가 처리한다.공평성은 유지하지만 중요한 작업이 중요하지 않은 작업을 기다리는 현상이 발생한다.
**2) 라운드 로빈(Round Robin)**
CPU를 할당받아 상요할 수 있는 시간을 일정한 고정된 시간으로 제한하여 처리한다.
할당되는 시간이 커지면 FCFS기법과 같아지고, 할당되는 작업이 작으면 Context-Switching이 자주 발생하여 효율성이 떨어진다.
**3) 우선순위(Priority)**
대기 중인 프로세스들에게 우선순위를 부여하고, 우선순위가 높은 프로세스에게 먼저 CPU 를 할당한다.


---
## 메모리 관리
* 물리적 메모리를 관리하는 방식에는 고정 분할 방식, 가변 분할 방식, 가상 메모리(Virtual Memory) 방식이 있다.
**1) 고정 분할 방식(Fixed Partition)** 
 물리적 메모리를 몇 개의 영구적인 분할로 나누고, 각각의 영역에 프로그램 
 하나씩 적재 시킨다.

**2) 가변분할 방식(Variable Partition)**
매 시점 프로그램 크기에 맞게 메모리를 분할한다.
물리적 메모리보다 큰 프로그램 실행이 불가능, 분할의 크기와 개수가 동적으로 변하므로 기술적 관리 기법이 필요하다.
필요한 크기만큼 메모리를 분할하므로 내부조각이 나지않지만, 외부 조각(external fragmentation) 이 발생할 수 있다.
예를 들어, 크기가 100인 프로그램 A가 실행되어 메모리에 100만큼 영역을 할당받음,
프로그램 A 실행중에 크기가 50인 프로그램 B가 실행되어 A 영역 바로 다음부터 메모리 50을 할당받음,
이때, A의 작업이 끝나 A의 영역에 크기가 80인 프로그램 C가 적재됨, 이때, 20만큼의 빈공간이 생기게 되는데, 
이후에 20보다 큰 프로그램들은 이 공간을 활용하지 못하게 되고, 계속 20만큼의 빈공간이 남음, 이것이 외부 조각!
​
**3) 가상 메모리 기법(Virtual Memory)**
용량이 작은 주기억장치를 마치 큰 용량을 가진 것 처럼 사용하는 기법. 물리적 메모리보다 큰 프로그램이 실행되는 것을 지원한다.
모든 프로그램은 물리적 메모리와는 독립적으로 주소가 0부터 시작하는 자신만의 가상 메모리를 가지게 된다.
운영체제는 가상 메모리의 주소를 물리적 메모리 주소로 매핑하는 기술을 이용해 주소를 변환 시킨 후 프로그램을 메모리에 올린다.
즉, 물리적 메모리가 5만큼 있고, 프로그램의 크기가 20이라고 할때, 프로그램 전체는 항상 동시에 사용되는 것이 아니기 때문에 현재 사용되고 있는 부분만 메모리에 올리고 나머지는 하드디스크와 같은 보조기억장치에 저장해 두었다가 필요할 때 적재하는 방식이다.