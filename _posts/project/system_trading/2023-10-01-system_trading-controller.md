---
title: System_Trading-Controller
date: 2023-10-01
categories: [Project, System_Trading]
tags: [_All, Finance]
---

## System_Trading Series

- [System_Trading-BluePrint](/posts/system_trading-blueprint/)

- [System_Trading-ETL](/posts/system_trading-etl/)

- [System_Trading-Model](/posts/system_trading-model/)

- [System_Trading-Controller](/posts/system_trading-controller/)

---

## 시스템 매매 Controller

시스템 매매 프로젝트에서 의사결정을 전송할 Controller를 구현한다.

---

## 매매 Platform

- 한국투자증권을 사용합니다.
  - API 거래가 가능
    - Open API 거래가 가능
    - Platform Independent

## Controller의 구현

### BaseController

BaseController를 먼저 구현합니다.

- 1차적인 Controller의 보안관련 설정을 세팅합니다.

```python
class BaseController:
    def __init__(self, api_key, api_secrete, account_no): ...
    def set_access_token(self):...
    def _check_access_token(self):...
    def _load_access_token(self):...
    def _set_access_token(self):...
    def _set_base_headers(self):...
```

### StatusController

StatusController는 현재 잔고 / 보유 종목의 상황을 파악합니다.

- 잔고 / 종목의 처리를 위해 데이터를 다루는 작업이 좀 필요합니다.

```python
class StatusController:
    def __init__(self, base_controller):...
    def fetch_balance(self, base_controller):...
    def fetch_orders(self, base_controller):...
    def fetch_position(self, base_controller):...

"""
ps) 
BaseController를 받아서 작업하는 형태
    fetch_balance는 잔고를 확인한다.
    fetch_orders는 예약주문을 확인한다.
    fetch_position는 현재 포지션(종목 / 수량 / 평단 / 수익률)을 확인한다.
"""
```

### OrderController

OrderController는 의사결정의 매수 / 매도를 진행합니다.

- 아무래도 추가적인 인증작업이 필요해 `StatusController`와 분리하였습니다.

```python
class OrderController:
    def __init__(self, base_controller):...
    def fetch_hashkey(self, base_controller):...
    def make_market_buy_order(self, base_controller):...
    def make_limit_buy_order(self, base_controller):...
    def make_market_sell_order(self, base_controller):...
    def make_limit_sell_order(self, base_controller):...

"""
ps)
BaseController를 받아서 작업하는 형태
    hashkey와 같이 시간에 dependent한 인증을 진행하며 주문을 해야합니다.
"""
```
