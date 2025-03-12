# 정규 표현식의 조건부 매칭

## 정확한 패턴의 필요성
정규 표현식으로 원하는 데이터를 정확히 찾기 위해서는 모호하지 않고 구체적인 패턴을 작성하는 것이 중요합니다. 예를 들어 "Buy more .*"와 같은 패턴은 너무 광범위하여 원치 않는 결과를 가져올 수 있습니다. 이런 경우 더 구체적인 조건부 매칭을 사용하면 정확성을 높일 수 있습니다.

## 파이프(|)를 사용한 조건부 매칭
정규 표현식에서는 **파이프(|)** 문자를 사용하여 여러 대안 중 하나와 매칭되도록 할 수 있습니다. 이는 "논리적 OR" 연산자와 같은 역할을 합니다.

### 기본 문법
- **A|B**: A 또는 B와 매칭
- **(pattern1|pattern2|pattern3)**: pattern1, pattern2, pattern3 중 하나와 매칭
- 여러 조건을 연속해서 사용 가능: **A|B|C|D**

## 조건부 매칭의 활용

### 단순 단어 선택
- **cat|dog**: "cat" 또는 "dog"와 매칭
- **Buy more (milk|bread|juice)**: "Buy more milk", "Buy more bread", "Buy more juice" 중 하나와 매칭
- **apple (pie|tart|cake)**: "apple pie", "apple tart", "apple cake" 중 하나와 매칭

### 복잡한 패턴과의 조합
- **([cb]ats*|[dh]ogs?)**: "cat", "cats", "bat", "bats", "dog", "dogs", "hog", "hogs" 등과 매칭
  - `[cb]ats*`: c 또는 b로 시작하고 "at"이 오고, s가 0개 이상 있는 패턴
  - `[dh]ogs?`: d 또는 h로 시작하고 "og"가 오고, s가 있거나 없는 패턴
- **(Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec) \d{1,2}, \d{4}**: 날짜 형식 매칭
  - "Jan 15, 2023", "Dec 25, 2023" 등과 매칭

## 그룹과 조건부 매칭의 결합
그룹화와 조건부 매칭을 함께 사용하면 더 강력한 패턴을 만들 수 있습니다.

### 중첩된 조건부 매칭
- **(small|large) (cat|dog)**: "small cat", "small dog", "large cat", "large dog" 매칭
- **I (love|hate) (coffee|tea) (with|without) (sugar|milk)**: 여러 조합의 문장 매칭

### 조건의 일부만 그룹화
- **prefix-(option1|option2)**: "prefix-" 뒤에 "option1" 또는 "option2"가 오는 패턴
- **\d{4}-(jpg|png|gif)**: "1234-jpg", "5678-png" 등과 같은 패턴

## 캡처 그룹과 조건부 매칭
조건부 매칭은 캡처 그룹과 함께 사용하면 매우 유용합니다.

### 조건부 내용 캡처
- **I need a (blue|red|green) (shirt|hat)**: 색상과 품목을 각각 캡처
  - "I need a blue shirt"에서 "blue"와 "shirt"를 캡처
- **(\d{4})-(jpg|png)**: 숫자와 확장자를 캡처
  - "1234-jpg"에서 "1234"와 "jpg"를 캡처

### 비캡처 그룹을 사용한 조건부 매칭
- **(?:http|https|ftp)://([\w-]+\.[\w.-]+)**: 프로토콜은 캡처하지 않고 도메인만 캡처
  - "https://example.com"에서 "example.com"만 캡처

## 가독성과 유지보수성
조건이 복잡해질수록 정규 표현식의 가독성이 떨어질 수 있습니다.

### 복잡한 조건부 패턴의 가독성 개선 방법
1. **여러 줄로 나누기**: 정규 표현식 엔진이 지원하면 주석과 함께 여러 줄로 작성
2. **별도의 패턴으로 분리**: 매우 복잡한 경우 여러 개의 작은 패턴으로 분리
3. **명명된 그룹 사용**: 지원하는 엔진에서는 그룹에 이름을 부여하여 가독성 향상

### 예시: 복잡한 조건부 패턴
```
# 복잡한 단일 패턴
(small|tiny|little)(cat|kitten|puppy)|(big|large|huge)(dog|wolf|bear)

# 분리하여 가독성 향상
smallPets = (small|tiny|little)(cat|kitten|puppy)
largePets = (big|large|huge)(dog|wolf|bear)
pattern = smallPets|largePets
```

## 작은 동물 매칭 예제
작은 동물들(small fuzzy creatures)만 매칭하는 패턴을 작성해봅시다.

### 조건부 패턴 작성
- **(mouse|hamster|gerbil|squirrel|chipmunk)**: 작은 동물들 중 하나와 매칭
  - "mouse", "hamster", "gerbil", "squirrel", "chipmunk"와 매칭

### 확장된 패턴
- **(small|tiny|little) (mouse|hamster|gerbil|squirrel|chipmunk)**: 작은 동물의 크기를 지정
  - "small mouse", "tiny hamster", "little squirrel" 등과 매칭

## 실용적인 활용 사례

### 다양한 파일 형식 매칭
- **\.(jpg|jpeg|png|gif|bmp)$**: 이미지 파일 확장자 매칭
- **\.(doc|docx|pdf|txt|rtf)$**: 문서 파일 확장자 매칭

### 프로그래밍 언어 키워드 매칭
- **(if|else|while|for|switch|case)**: 프로그래밍 언어 키워드 매칭
- **(public|private|protected) (class|interface|enum)**: Java 클래스 정의 매칭

### 통화 및 측정 단위
- **\d+(\.\d+)? (USD|EUR|GBP|JPY)**: 통화 금액과 단위 매칭
- **\d+(\.\d+)? (cm|mm|m|km|inch|ft)**: 길이 측정과 단위 매칭

## 실습 예제
다음과 같은 조건부 패턴을 작성해 보세요:

1. 과일과 채소 목록 매칭:
   - `(apple|banana|orange|grape|strawberry)|(carrot|broccoli|spinach|lettuce)`
   - 과일 그룹과 채소 그룹을 각각 매칭

2. 다양한 프로그래밍 언어 파일 확장자:
   - `\.(py|java|js|ts|php|rb|c|cpp|cs|go)$`
   - 여러 프로그래밍 언어의 소스 파일 확장자 매칭

## 주의사항
1. 조건이 복잡하고 많아질수록 성능에 영향을 줄 수 있습니다
2. 가능하면 문자 클래스(`[abc]`)가 더 효율적인 경우 이를 우선 사용하세요 (예: `[abc]`는 `(a|b|c)`보다 효율적)
3. 조건부 매칭은 괄호로 그룹화하는 것이 좋습니다 (우선순위와 명확성을 위해)
