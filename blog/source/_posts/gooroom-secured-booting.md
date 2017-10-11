---
title: gooroom-secured-booting
date:
tags:
layout: post
permalink: gooroom-secured-booting
---

구름 신뢰부팅 기술
===============

구름 신뢰부팅 기술은 시스템이 안전한 상태에서 동작을 시작하도록 보장합니다.
* 구름 신뢰부팅 기술 v1.0: 구름 신뢰부팅 기술 v1.0은 UEFI Secure Boot를 바탕으로 하며 구름플랫폼 v1.0에 적용된 기술입니다.
* 구름 신뢰부팅 기술 Beta (deprecated): 구름 신뢰부팅 기술 Beta는 BIOS로 부팅하는 단말을 위해 개발되었으며, 구름플랫폼 베타버전에 적용된 기술입니다. 이 기술은 더 이상 업데이트되지 않습니다.

구름 신뢰부팅 기술 v1.0
---------------
구름 신뢰부팅 기술 v1.0은 UEFI로 부팅하는 환경에서 시스템이 안전하게 부팅할 수 있도록 지원합니다. 구름 신뢰부팅 기술 v1.0의은 다음과 같이 동작합니다.

![구름 신뢰부팅 기술 v1.0의 동작](/images/gooroom-secured-booting.png)

* 단계 1: [UEFI](http://www.uefi.org/specifications) 펌웨어는 실행할 Gooroom GRUB 부트로더의 서명이 유효한지 확인합니다. 서명 유효성 검증에 실패할 경우 부팅을 거부하고 종료합니다. 서명 검증에 필요한 키는 관리자가 각 단말의 UEFI 메뉴를 통해 등록해야 합니다.
* 단계 2: Gooroom GRUB 부트로더는 커널 및 주요 파일들(initrd, grub.conf)의 서명이 유효한지 확인합니다. 서명 유효성 검증에 실패할 경우 부팅을 거부하고 종료합니다.
