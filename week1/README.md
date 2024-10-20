# 프리코스 1주 미션 회고

## 🗓️기간 
+ 2024-10-15 ~ 2024-10-21

## 🧑🏻‍💻미션 회고
우테코 첫번째 미션 "문자열 덧셈 계산기"는 앞으로 하게 될 미션을 포함해서 난이도가 가장 쉬운 요구사항을 가진 미션이라고 생각되는데, 
생각보다 쉽지만은 않았습니다. 일단 코드를 작성하기에 앞서 README에 구현해야 하는 기능 목록을 작성해야 하며, 
무엇보다 기능 단위로 커밋을 해야 하는 요구사항을 지키는 것이 까다로웠습니다. 
하지만 기능 단위로 분리하다 보니 커밋이 명확해지는 장점을 느낄 수 있었습니다. 
차후에 롤백을 해야할 경우에도 형상관리를 함에 있어 효과적일 것 같습니다.
다음 미션은 조금 더 상세하게 기능 분리를 해서 기능 목록을 작성해야 커밋 단위를 나누는 데에 더 수월할것 같습니다.

그리고 코드를 TDD로 처음 구현해 보니, 장점도 있고 단점도 있었습니다.
장점은 테스트 코드를 먼저 작성하기 때문에 코드의 품질이 향상되는 것을 느낄 수 있었습니다. 
또한, 자연스럽게 테스트 코드가 많아져 프로그램 기능 오류들을 디버깅할 때 생산성을 느꼈습니다.
단점은 패키지 구조와 네이밍에 대해서 신경을 많이 쓰기 때문에 많은 리팩토링이 일어나 TDD로 구현했던 부분이 많이 손실되거나 수정되는 것입니다.
그렇지만, 큰 단점이라고는 생각하지 않아 성장을 위해 계속되는 미션에서도 TDD로 구현해 볼 것입니다.

다음 미션은 요구사항이 더 많아질 것 같은데 준비 잘해서 마무리 잘했으면 좋겠습니다.

## 특이 사항 
+ 구분자의 중복이 일어나지 않게 `Set`컬렉션을 사용하다. 
```java
public class BasicDelimiter {

    public static final String COMMA = ",", COLON = ":";

    public static Set<String> getBasicDelimiters() {
        return Set.of(COMMA, COLON);
    }
}
```
+ `\` 이스케이프를 허용하기 위해 구분자로 문자열을 리스트로 변환할 시에, `Patter::quote`를 사용하다. 
```java
private String getDelimiterRegex(Set<String> delimiters) {
    return delimiters.stream()
            .map(Pattern::quote)
            .collect(joining("", "[", "]"));
}
```
+ 요구사항의 양수의 범위가 지정되지 않아 `BigInteger`타입으로 선언
```java
public class StringToPositiveBigIntegerConverter {

    public BigInteger convert(String number) {
        try {
            BigInteger result = new BigInteger(number);

            if (result.compareTo(ZERO) <= 0) {
                throw new IllegalArgumentException(NOT_POSITVE_INTEGER.getMessage());
            }

            return result;
        } catch (NumberFormatException e) {
            throw new IllegalArgumentException(INVALID_BIG_INTEGER.getMessage());
        }
    }
}
```




