# GPT와 Transformer 기술 개요 및 ChatGPT API 사용법

## 1. GPT란?
### 정의
- **GPT**는 **Generative Pre-trained Transformer**의 약자로, OpenAI에서 개발한 자연어 처리(NLP) 모델입니다.
- 주요 특징:
  - **Generative(생성형)**: 텍스트 생성, 번역, 요약 등 다양한 작업 가능.
  - **Pre-trained(사전 학습)**: 대규모 데이터로 사전 학습 후 특정 작업에 바로 활용 가능.
  - **Transformer 기반**: Transformer 구조를 통해 높은 성능을 발휘.

---

## 2. Transformer와 Attention 메커니즘
### Transformer란?
- 구글의 논문 **"Attention is All You Need"**(2017)에서 처음 소개된 모델.
- 주요 특징:
  - **병렬 처리**: RNN보다 빠른 학습 속도.
  - **장기 의존성 학습**: 멀리 떨어진 단어 간의 관계를 효과적으로 학습.
- 주요 구성 요소:
  - **인코더(Encoder)**: 입력 데이터를 이해하고 내재화.
  - **디코더(Decoder)**: 내재화된 데이터를 바탕으로 출력 생성.

### Attention 메커니즘
- 텍스트에서 중요한 단어에 집중하는 기술.
- **Self-Attention**:
  - 텍스트 내 단어 간의 관계를 학습.
  - 예: "그녀는 책을 읽었다. 그녀는 행복해 보였다."에서 "그녀"가 문맥 속 다른 단어와 연결되는 방식 학습.

---

## 3. ChatGPT API 사용법

### API란?
- **API**(Application Programming Interface): 프로그램 간 상호작용을 위한 인터페이스.
- 주요 역할:
  - 데이터 요청 및 전달.
  - 작업 수행.
  - 표준화된 인터페이스 제공.

### ChatGPT API 개요
- OpenAI에서 제공하는 서비스로, GPT 모델의 언어 생성 기능을 애플리케이션에 통합 가능.

### API 키 발급 및 설정
1. OpenAI API 포털 가입 후 API 키 생성.
2. **API 키 보안**:
   - 개인 키를 타인과 공유하지 않도록 주의.
   - 요금이 부과될 수 있음.

### Python으로 API 호출 예제
```python
import openai

# API 키 설정
openai.api_key = "your_api_key_here"

# API 요청
response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "당신은 사용자 질문에 답변하는 챗봇입니다."},
        {"role": "user", "content": "안녕, 너에 대해서 설명해줄래?"}
    ]
)

# 응답 출력
print(response.choices[0].message.content)
```
### 주요 매개변수
- model: 사용하려는 GPT 모델의 이름.
- messages: 대화 히스토리.
- role: 메시지 작성 주체(system, user, assistant).
- content: 메시지 내용.
- max_tokens: 응답의 최대 토큰 수.
- temperature: 응답의 창의성 조정(0~2, 높을수록 창의적).
- top_p: 출력 다양성 조정(0~1, 1에 가까울수록 다양함).
- n: 생성할 응답의 개수.
### API 응답 데이터 구조
- id: 요청 ID.
- choices: 모델의 응답 리스트.
- usage: 토큰 사용량 정보.
---
## 4. GPT의 한계
- 정확성 부족: 잘못된 정보를 생성할 가능성(할루시네이션).
- 훈련 데이터 의존: 사전 학습 데이터에 없는 정보는 처리 불가.
- 편향성: 학습 데이터에 포함된 편향이 반영될 가능성.

---
## 5. 마무리
- GPT는 텍스트 생성, 번역, 요약 등 다양한 작업에서 강력한 도구로 활용 가능.
- ChatGPT API는 개발자가 쉽게 언어 생성 기능을 애플리케이션에 통합할 수 있도록 지원.
