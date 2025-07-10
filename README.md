<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:7f7fd5,50:86a8e7,100:91eae4&height=200&text=🧠%20Brain-Trace&fontSize=45&animation=fadeIn&fontColor=ffffff" />
</p>

<div align="center">
AI가 학습 자료를 자동 분석하고  
<br>
<strong>당신만의 Second Brain</strong>으로 만들어드립니다.
</div>

---
## 🧠 프로젝트 개요

> **“자료를 넣으면 지식이 된다. 질문하면 문맥이 답한다.”**

현대의 학습 환경에서는 수많은 학습 자료(PDF, 강의 녹음, 텍스트 파일 등)가 디지털화되어 존재하지만,  
이를 체계적으로 정리하고 활용하는 데에는 여전히 **사람의 수작업**이 필요합니다.  
또한 개인 맞춤형 학습 도우미는 대부분 **클라우드 기반 서비스**로, **보안성**과 **개인정보 보호** 측면에서 한계가 존재합니다.

**Brain-Trace**는 이러한 문제를 해결하기 위해 기획된 **온디바이스 지식그래프 기반 AI 도우미**입니다.  
사용자가 PDF, 텍스트, 음성 파일을 업로드하면 시스템은 자동으로 내용을 분석하고,  
핵심 개념과 관계를 추출하여 **지식그래프(Knowledge Graph)** 형태로 구조화합니다.

이후 사용자가 자연어로 질문하면, 내부적으로 **온디바이스 LLM을 사용하여 Cypher 쿼리로 변환**하고,  
**Neo4j 데이터베이스에서 관련 정보를 검색**한 후, **출처 기반의 문맥 응답**을 제공합니다.  
이는 기존의 단순 요약 시스템과 달리 **질문자의 의도에 따라 다단계 추론과 연결 정보**를 바탕으로  
정확한 정보를 제공할 수 있어, 학습의 질을 크게 향상시킵니다.

또한 모든 프로세스는 로컬 디바이스에서 처리되므로,  
**클라우드 의존 없이 완전한 오프라인 환경에서도 작동**하며,  
**개인정보 보호 및 민감한 연구자료의 안전한 처리**가 가능합니다.

📌 결과적으로, Brain-Trace는 단순한 문서 분석 도구를 넘어 
"내 손안의 두 번째 뇌(Second Brain)"로서 작동하는  
**지식 구조화 + 문맥 질문 응답 + 보안 강화**의 종합 AI 시스템입니다.

---

## 🌟 주요 기능

### 🔐 온디바이스 기반 AI
- 모든 기능은 **클라우드 없이 로컬에서 실행**
- 개인정보 유출 우려 없이 **보안성과 비용 절감** 실현

### 📄 다양한 자료 자동 분석
- **PDF, 텍스트, 음성**을 업로드하면 자동으로 정보 추출  
- 자연어 처리로 **개념(노드)**과 **관계(엣지)**를 생성하여 **Neo4j 그래프**에 저장

### 🧠 지식그래프 시각화
- **Cytoscape.js** 기반으로 직관적인 **그래프 탐색** 제공  
- 노드 클릭/하이라이팅 기능으로 **문맥 추적** 용이

### 💬 RAG 기반 문맥 질의응답
- 사용자의 질문을 **온디바이스 LLM을 통해 Cypher 쿼리로 변환**  
- **Graph DB에서 응답 추출 + 출처 제공**  
- 단순 요약을 넘어 **구조 기반의 정밀한 답변** 제공

### 🔍 출처 기반 응답 인터페이스
- 답변에 사용된 **지식 노드 출처**를 함께 제공  
- 정보 신뢰성과 **추적 가능성** 향상

---

## 🧬 시스템 아키텍처

```text
[문서 업로드]
      ↓
[텍스트/음성 분석 (Whisper, NLP)]
      ↓
[개체/관계 추출 → Neo4j 저장]
      ↓
[사용자 질의 (자연어)]
      ↓
[온디바이스 llm 기반 Cypher 쿼리 생성]
      ↓
[Neo4j에서 응답 추출 + 출처 추적]
      ↓
[문맥 기반 답변 + 노드 시각화]
```

---

## 🛠️ 기술 스택

| 항목 | 기술 |
|------|------|
| 프론트엔드 | React, Cytoscape.js, Vite |
| 백엔드 | FastAPI |
| 데이터베이스 | Neo4j (Embedded), SQLite |
| 음성 인식 | OpenAI Whisper |
| AI 모델 | llama, KoE5 |
| RAG 구성 | 자연어 → Cypher → Graph 응답 |
| 기타 도구 | Electron, VS Code, Git |

---

## 📑 API 문서 (Swagger UI)

<details>
<summary>📂 Swagger Docs 보기 (클릭해서 펼치기)</summary>

<br>

FastAPI 기반 REST API는 아래와 같은 Swagger UI 형태로 구성되어 있습니다.

<p align="center">
  <img src="https://github.com/yes6686/portfolio/blob/main/Swagger_API.png?raw=true" alt="Swagger UI Screenshot" width="85%" />
</p>

> 로컬에서는 `http://localhost:8000/docs`에서 직접 확인하실 수 있습니다.

</details>

---

## 🧪 성능 비교 (Graph-RAG vs 일반 RAG)

| Method | P | R | F1 |
|--------|----|----|----|
| **Community-GraphRAG (Local)** | **67.2** | **64.89** | **64.6** |
| 일반 RAG | 66.34 | 63.99 | 63.88 |

> 출처: [arXiv:2502.11371](https://doi.org/10.48550/arXiv.2502.11371)

---

## 💡 기대 효과

- 📚 **교육용 AI 학습 도우미**  
  - 강의자료 기반 자동 정리 및 질문 응답 지원
- 🏢 **기업 지식관리 도구**  
  - 회의록/문서 자동 구조화, 검색 효율성 향상
- 🔒 **보안 중심 AI**  
  - 인터넷 연결 없이 사용 가능한 **오프라인 AI 플랫폼**
    
---
## 🎥 시연 영상

| 소개 영상 | Demo Video |
|-----------|------------|
| [![Brain-Trace 소개](https://img.youtube.com/vi/Q0w4S_sMEaQ/0.jpg)](https://www.youtube.com/watch?v=Q0w4S_sMEaQ) | [![Brain-Trace Demo](https://img.youtube.com/vi/r6AdiX7SZkw/0.jpg)](https://www.youtube.com/watch?v=r6AdiX7SZkw) |

---

<details>
<summary>📊 시스템 구조 패널 보기 (클릭해서 펼치기)</summary>

<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3c98fd2c-b38e-4ede-9704-d518111129e1" alt="시스템 구조 패널" width="80%"/>
</p>

</details>

## 🔗 참고 자료

- [React 공식 문서](https://reactjs.org/docs/getting-started.html)
- [Neo4j 공식 문서](https://neo4j.com/docs/)
- [OpenAI Whisper](https://github.com/openai/whisper)
- [GPT API Docs](https://platform.openai.com/docs/)
- [GraphRAG 논문](https://arxiv.org/abs/2502.11371)

---


## 👥 팀원 소개

| 이름       | 역할                   | 담당 업무                                                                                  |
|------------|------------------------|---------------------------------------------------------------------------------------------|
| **김동혁** | Back-End               | FastAPI 기반 API 개발, 검색/답변/지식그래프 생성 로직 개발,<br>Graph DB & SQLite 설계     |
| **안예찬** | Front-End              | Note 패널, 소스 뷰어, 로컬 DB 연동 UI 구현                                                  |
| **유정균** | AI                     | AI 모델 양자화 및 경량화                                                                    |
| **정웅**   | 팀장 / Front-End & AI | 프로젝트 총괄, 프론트엔드 개발,<br>AI 및 Graph DB 연동                                       |
=======
## 📃 라이선스

```
Copyright (c) 2025 Brain-Trace Team
All rights reserved.

This code is provided for academic, non-commercial use only.
Redistribution and use in source and binary forms, with or without modification,
are permitted for academic non-commercial use provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice,
   this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation and/or
   other materials provided with the distribution.

This software is provided by the authors "as is" and any express or implied warranties,
including, but not limited to, the implied warranties of merchantability and fitness
for a particular purpose are disclaimed. In no event shall the authors be liable
for any direct, indirect, incidental, special, exemplary, or consequential damages
(including, but not limited to, procurement of substitute goods or services;
loss of use, data, or profits; or business interruption) however caused and on
any theory of liability, whether in contract, strict liability, or tort (including
negligence or otherwise) arising in any way out of the use of this software,
even if advised of the possibility of such damage.

```

