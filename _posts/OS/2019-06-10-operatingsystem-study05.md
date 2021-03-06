---
layout: post
title:  "3-2. 프로세스와 스레드"
date:   2019-06-10
author: YoungHwan Kim
categories: OS
comment : true
tags:	운영체제 OpeartingSystem OS
cover:  ""
---


### 6. 문맥교환

- 트랩은 부적절한 파일 접근이나 현재 실행 중인 프로세스에 의해 발생되는 오류나 예외 상황 때문에 발생한다.

- 인터럽트의 대표적인 예.
   - 입출력 인터럽트 : 입출력 동작이 발생한 사실을 확인한 후 이벤트를 기다리는 프로세스를 준비 상태로 바꾸고 실행할 프로세스를 결정한다.
   - 클록 인터럽트 : 현재 실행 중인 프로세스의 할당 시간을 조사하여 실행 중인 프로세스를 준비상태로 바꾸고 다른 프로세스를 디스패치하여 실행 상태로 바꾼다.

- 프로세스를 다른 프로세스로 교환하려면 이전 프로세스의 상태 레지스터 내용을 보관하고 다른 프로세스의 레지스터를 적재해야 하는데, 이런 일련의 과저을 문맥교환(Context Switching)이라 한다. 
- 예를 들어 프로세스가 '준비->실행'  or '실행->준비' or '실행->대기' 상태로 변할 때 문맥교환이 발생한다.

- 현대의 운영체제는 스레드(Thread)를 이용하여 문맥교환을 효율적으로 처리한다. 

