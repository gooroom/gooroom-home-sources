---
title: executables-protection
date: 2017-10-10 10:45:11
tags:
---

구름 실행파일 보호 기술
===============

구름 보안 프레임워크는 리눅스의 무결성 측정 구조([Integrity Measurement Architecture](https://sourceforge.net/p/linux-ima/wiki/Home/))를 사용하여 실행파일을 실행하거나 커널 모듈을 적재하기 전 파일의 서명이 유효한지 검증합니다. 관리자는 보호할 파일을 지정하고 서명할 필요가 있습니다. 관리자의 서명, 보다 정확하게는 파일의 해쉬값에 대한 서명 값은 해당 파일의 확장속성(Extended attributes, [xattr](http://man7.org/linux/man-pages/man7/xattr.7.html))에 저장됩니다.
이후, 해당 파일을 메모리에 로드하기 전, 리눅스 보안 모듈(LSM, Linux Security Module)에 의해 서명 검증 절차가 활성화되며, 유효성 검증에 실패한 파일은 실행이 거부됩니다.
