# learning regular expressions

## 개요
정규 표현식(Regular Expressions)을 학습하기 위한 개인 아카이빙입니다.


## 학습 내용

1. **[정규 표현식 소개](01_regex_introduction.md)**
   - 정규 표현식의 정의와 목적
   - 기본 원리와 사용 문자
   - 활용 분야

2. **[숫자와 메타문자](02_regex_numbers_and_metacharacters.md)**
   - 숫자의 이해와 매칭
   - 메타문자 소개 (\d)
   - 문자열 내 매칭 위치

3. **[특정 문자 매칭](03_regex_specific_characters.md)**
   - 대괄호([])를 사용한 문자 집합
   - 점(.) 메타문자의 한계
   - 정교한 패턴 매칭 방법

4. **[특정 문자 제외](04_regex_excluding_characters.md)**
   - 캐럿(^)을 사용한 문자 제외 방법
   - 포함 방식과 제외 방식의 비교
   - 실제 응용 사례

5. **[문자 범위](05_regex_character_ranges.md)**
   - 하이픈(-)을 사용한 문자 범위 지정
   - 다중 문자 범위와 개별 문자 조합
   - \w 메타문자와 대소문자 구분

6. **[문자 반복](06_regex_character_repetition.md)**
   - 중괄호({})를 사용한 반복 횟수 지정
   - 정확한 횟수와 범위 지정
   - 반복 패턴의 실제 응용 사례

7. **[Kleene 연산자](07_regex_kleene_operators.md)**
   - Kleene Star(*)와 Kleene Plus(+) 이해하기
   - 임의 개수 문자 매칭 방법
   - 실제 응용 사례와 주의사항

8. **[선택적 문자](08_regex_optional_characters.md)**
   - 물음표(?)를 사용한 선택적 문자 지정
   - 복수형/단수형 및 변형 단어 매칭
   - 이스케이프된 물음표(\?) 사용법

9. **[공백 문자](09_regex_whitespace_characters.md)**
   - 다양한 종류의 공백 문자 이해하기
   - \s 메타문자의 활용
   - 실제 데이터에서 공백 처리 방법

10. **[앵커 문자](10_regex_anchors.md)**
    - 캐럿(^)과 달러($) 기호를 사용한 위치 지정
    - 문자열 시작과 끝 매칭하기
    - 정확한 패턴 매칭과 오탐 방지

11. **[매칭 그룹](11_regex_match_groups.md)**
    - 소괄호(())를 사용한 캡처 그룹 지정
    - 텍스트에서 정보 추출하기
    - 역참조와 비캡처 그룹

12. **[중첩 그룹](12_regex_nested_groups.md)**
    - 그룹 안의 그룹 구성하기
    - 계층적 데이터에서 정보 추출
    - 그룹 번호 매기기와 참조 방법

13. **[고급 그룹 활용법](13_regex_advanced_groups.md)**
    - 캡처 그룹과 수량자 결합하기
    - 비캡처 그룹(Non-capturing Groups) 활용
    - 그룹 내 대체(Alternation) 패턴 사용

14. **[조건부 매칭](14_regex_conditionals.md)**
    - 파이프(|)를 사용한 OR 조건
    - 여러 대안 중 하나와 매칭하기
    - 복잡한 조건부 패턴과 가독성

15. **[캡처 그룹 vs 문자 집합](15_regex_capture_groups_vs_character_sets.md)**
    - 소괄호(())와 대괄호([])의 차이점
    - 그룹화와 문자 선택의 구분
    - 두 개념의 조합 활용법
