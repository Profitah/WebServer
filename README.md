## 공동작업자

| [<img src="https://github.com/wonsanha98.png?size=100" width="100px;"> <br> <sub>산하 형님</sub>](https://github.com/wonsanha98) | [<img src="https://github.com/JOJoungMin.png?size=100" width="100px;"> <br> <sub>정민 형님</sub>](https://github.com/JOJoungMin) |
|---|---|


---

### **구현한 것**: *Tiny Echo Proxy*

---

### 개인 발표 주제

우리는 **프록시 서버 구현에 성공했다!** 🎉


### 확인 사항
프록시를 경유할 때 발생하는 **외부 CDN(JS 라이브러리) 로딩 실패 현상**을 재현함으로써, 프록시 서버 구현에서 중요한 요소(CORS, 헤더 처리, 연결 관리 등)의 필요성을 검증하였다.

---

### 시나리오
* **흐름**: Client → Proxy → MDN/CDN
* **실험 방법**: 프록시가 응답에서 `Access-Control-Allow-Origin` 헤더를 **의도적으로 제거** → 브라우저 차단 유도

---

### 관찰된 증상

* JS 파일 로딩 실패 (404/403, 부분 전송, **CORS 오류**)
* `<script type="module">`은 CORS 검증이 필수 → 헤더 누락 시 즉시 차단 발생

---

### 결론 및 시사점

* CDN은 기본적으로 CORS 허용 헤더를 제공하므로 원래는 정상 로딩됨
* 그러나 프록시 서버가 해당 헤더를 누락시키면 즉시 로딩 실패 발생
* 본 시연은 **프록시 서버를 직접 구현했고, 그 동작 특성을 검증했다는 명확한 증거**
