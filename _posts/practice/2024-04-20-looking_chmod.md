---
title: chmod를 살펴보자
date: 2024-04-20
categories: [Practice, Linux]
tags: [Looking, Linux]
---

## 권한

권한의 종류
    - r : read
    - w : write
    - x : execute

## 유저

유저의 종류
    - u : user (본인)
    - g : group (그룹)
    - o : others (다른유저)
    - a : all (전체)

## 간단한 예시

```plaintext
drwxr-xr-x⠀staff⠀64⠀Apr 24 19:03:26⠀ ⠀my_dir/
-rw-r--r--⠀staff⠀0 ⠀Apr 24 19:03:32⠀ ⠀my_file_01
-rw-r--r--⠀staff⠀0 ⠀Apr 24 19:03:43⠀ ⠀my_file_02
-rw-r--r--⠀staff⠀0 ⠀Apr 24 19:03:44⠀ ⠀my_file_03
0123456789

권한의 해석
    0 : is_directory    (d / -)
    1 : User   : read     (r / -)
    2 : User   : write    (w / -)
    3 : User   : execute  (e / -)
    4 : group  : read     (r / -)
    5 : group  : write    (w / -)
    6 : group  : execute  (e / -)
    7 : others : read     (r / -)
    8 : others : write    (w / -)
    9 : others : execute  (e / -)
```
