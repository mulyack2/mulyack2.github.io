---
title: 맥북 ssh 외부접속 허용하기, ssh-key를 통한 인증하기
date: 2024-05-01
categories: [Think, Linux]
tags: [_All, Linux]
---

## 서론

`맥북 에어`를 하나 획득하였습니다.

기존에 `맥북 프로`가 있고, 컴퓨터 클러스터링 및 클라우드 네이티브를 위한 노력의 일환으로 구매했는데요.

기존 `맥북 프로`를 집에 클램쉘 모드로 사용하고 대체로 맥북에어를 통한 작업을 진행하려고 합니다.

이를 위해 기존 `맥북 프로`의 ssh 포트를 열고 적절한 보안 설정을 진행했습니다.

## 본론

진행사항

- [ ] 원격접속 허용하기
- [ ] 포트 열기

--- 비밀번호를 통한 접속 완료 ---

- [ ] ssh-key를 통한 보안 설정하기

--- ssh-key 보안 설정 완료 ---

### 1. 원격접속 허용하기

![fig](/assets/img/_posts/think/mac-ssh-external/remote_connect.png)

가장 먼저 맥북의 remote 접속을 허용합니다.

이렇게 되면 `내부 IP`간 ssh 접속이 가능합니다.

```plaintext
같은 IP안에 있다면 ssh 접속 가능
Ex)
  집에서
    [맥북 에어]로 [맥북 프로]에 ssh 접속이 가능하다.
  카페에서
    [맥북 에어]로 [맥북 프로]에 ssh 접속은 불가하다.

ssh user@[your private ip] -p 22
```

### 2. 외부 포트 열기

![fig](/assets/img/_posts/think/mac-ssh-external/port_forward.png)

이렇게 되면 `외부 IP`에서 ssh 접속이 가능합니다.

이 상태로 외부에서 접속을 진행하면

```plaintext
ssh user@[your public ip] -p 22
```

### 3. ssh-key

```bash
sudo vi /etc/ssh/sshd_config

# add below

PubKeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
PermitRootLogin no
PasswordAuthentication no
ChallengeResponseAuthentication no
```

이렇게 작업하면 이제 password로는 접속이 불가하고, ssh-key를 통한 접속만 가능하다.
