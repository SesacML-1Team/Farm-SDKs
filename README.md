# Farm-SDKs

SDK implementations for Azure resources.

## Repository layout

- `openai_compliance.py`: Azure OpenAI + Azure AI Search 예제입니다. 전라도(전라남도/전라북도) 지역의 귀농귀촌 정책 질의를 대상으로, RAG 데이터 소스에서 "귀농귀촌"이 포함된 PDF만 참고하도록 엄격한 시스템 프롬프트를 구성합니다. 응답은 JSON 포맷으로 출력하도록 되어 있습니다.
- `openai_field.py`: Azure OpenAI + Azure AI Search 예제입니다. "농지_전처리완료.csv" 기반의 매물 추천 시나리오를 가정하고, 입력 지역과 가까운 매물 정보를 정해진 출력 포맷으로 반환하도록 시스템 프롬프트가 구성되어 있습니다.

## 실행 방법

1. Azure OpenAI 리소스의 엔드포인트와 배포 이름을 확인합니다.
2. Azure AI Search 인덱스 및 키 값을 준비합니다.
3. 각 스크립트의 아래 값을 실제 환경에 맞게 수정합니다.
   - `endpoint`, `deployment`
   - `search_endpoint`, `search_index`, `search_key`
   - `subscription_key`
4. 스크립트를 실행합니다.

```bash
python openai_compliance.py
python openai_field.py
```

## Notes

- 두 스크립트는 모두 Azure OpenAI 엔드포인트와 Azure AI Search 인덱스를 사용하도록 설계되어 있습니다. 실제 실행 시에는 `subscription_key`와 `search_key`를 유효한 값으로 교체해야 합니다.
- `openai_compliance.py`는 `farm-compliance` 인덱스에 있는 "귀농귀촌" PDF만 참조하도록 시스템 프롬프트에 제약이 포함되어 있습니다.
- `openai_field.py`는 `house-toji-rag` 인덱스를 대상으로 하며, 매물 정보는 "농지_전처리완료.csv"의 컬럼 구성에 맞춰 정리됩니다.
- `__main__` 블록에 포함된 샘플 입력은 동작 확인용으로 제공됩니다.
