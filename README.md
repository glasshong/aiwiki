# aiwiki

ML과 DL 중심으로 AI 지식을 정리하는 Markdown 기반 문서 사이트입니다. MkDocs로 로컬 웹사이트처럼 열어볼 수 있고, 내용은 `docs/` 아래의 Markdown 파일에 계속 추가하면 됩니다.

## 구조

- [ML](docs/ml/index.md)
- [DL](docs/dl/index.md)
  - [Train](docs/dl/train/index.md)
  - [Vision](docs/dl/vision/index.md)
  - [NLP](docs/dl/nlp/index.md)
  - [Optimization](docs/dl/optimization/index.md)

## 작성 방식

각 문서는 아래 흐름으로 정리합니다.

1. 한 줄 정의
2. 왜 중요한가
3. 핵심 개념
4. 자주 헷갈리는 점
5. 손계산 또는 작은 예제
6. 관련 개념 링크

## 웹사이트로 보는 방법

```powershell
pip install mkdocs
mkdocs serve
```

실행 후 브라우저에서 아래 주소를 열면 됩니다.

```text
http://127.0.0.1:8000
```

정적 파일로 빌드하려면:

```powershell
mkdocs build
```

빌드 결과는 `site/` 폴더에 생성됩니다.

## 참고 출처

- AI by Hand, Prof. Tom Yeh: https://www.byhand.ai/
- Transformer - Six Levels of Understanding: https://www.byhand.ai/p/transformer-six-levels-of-understanding
- AI by Hand Academy 소개: https://www.byhand.ai/p/ai-by-hand-academy-5ec
