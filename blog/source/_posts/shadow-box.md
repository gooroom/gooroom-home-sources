---
title: shadow-box
date: 2017-10-12 09:51:22
tags:
---

경량 하이퍼바이저 기반 OS 보호 기술
===============

경량 하이퍼바이저
---------------
구름플랫폼이 사용하는 경량 하이퍼바이저는 CPU가 제공하는 가상화 기술(VT: Virtualization Technology)을 사용하므로 견고하고 효율적입니다. 또한 다음과 같은 특징을 가집니다.
* 모듈형태로 개발하여 구름플랫폼이 이미 설치된 환경에서도 OS의 재설치 없이 사용할 수 있습니다.
* 일반적으로 널리쓰이는 가상화 시스템들과 달리, OS 보호를 위해 최소한의 가상영역을 생성하므로 성능 및 공간 부담이 거의 없습니다.

경량 하이퍼바이저 기반 OS 보호 기술: Shadow-Box
---------------
루트킷과 같이 시스템 권한으로 동작하는 악성코드들은 백신 이나 감사프로세스로부터 자신을 숨기기 위해, 또는 백도어를 설치하거나 시스템 오동작을 유발하기 위해 태스크 목록, 모듈 목록, 네트워크 연산 포인터, 파일 연산 포인터 등의 OS 내부 자료구조를 위조 또는 변조합니다.

Shadow-Box는 구름플랫폼이 시작할 때 로드되어 OS 내부 자료구조의 무결성 훼손 여부를 감시하고 차단합니다. Shadow-Box는 하이퍼바이저모드로 동작하며, 시스템 권한 악성코드들로부터 안전하게 시스템을 보호합니다.

Shadow-Box의 기술적 세부사항 및 우수성은 다음 발표자료들을 통해 확인하실 수 있습니다.
* Black Hat Asia 2017: [Myth and Truth About Hypervisor-Based Kernel Protector: The Reason Why You Need Shadow-Box](https://www.blackhat.com/asia-17/briefings/schedule/#myth-and-truth-about-hypervisor-based-kernel-protector-the-reason-why-you-need-shadow-box-5283)
* HitBSecConf 2017: [Shadow-Box: The Practical and Omnipotent Sandbox](https://conference.hitb.org/hitbsecconf2017ams/sessions/shadowbox-the-practical-and-omnipotent-sandbox/)

Shadow-Box 설치 및 실행
---------------
Shadow-Box는 구름매니저를 통해 설치하고 실행할 수 있습니다.
자세한 내용은 앞으로 업데이트 할 예정입니다. 

주의
---------------
경량 하이퍼바이저 사용을 위해 다음과 같은 내용을 확인하십시오.
* CPU의 VT 지원 여부: 경량하이퍼바이저는 현재 Intel의 VT기술을 활용하여 구현하고 있습니다. 설치할 단말의 CPU가 VT기술을 지원하는지 확인할 필요가 있습니다 ([Does My Processor Support Intel® Virtualization Technology?](https://www.intel.com/content/www/us/en/support/articles/000005486/processors.html))
* 다른 가상화 소프트웨어 사용 계획: 경량 하이퍼바이저는 시스템 실행시간에 Intel VT기술을 독점 사용하며, 중첩 가상화 방식을 지원하지 않습니다. 따라서 VMware, VirtualBox, KVM 등 하드웨어의 가상화 가속 기능을 사용하는 소프트웨어와 함께 사용할 수 없습니다. 이진변환 기술을 사용하는 qemu와의 병용은 시험된 바 없습니다.
