# CSRF, XSS 방어

### CSRF(Cross-Site Request Forgery)란?

CSRF(Cross-Site Request Forgery)는 웹 애플리케이션 보안 공격의 하나로, 공격자가 희생자의 권한을 이용하여 **특정 동작(예: 계정 변경, 글 게시 등)을 실행하도록 속이는 공격**이다. 이 공격은 사용자가 악성 웹 사이트를 방문하거나 이메일을 통해 **악성 링크를 클릭했을 때 발생**할 수 있다.

### XSS(Cross-Site Scripting)란?

XSS (Cross-Site Scripting)는 웹 애플리케이션 보안 공격의 하나로, **공격자가 악의적인 스크립트 코드를 웹 페이지에 삽입하는 공격**이다. 이 스크립트 코드는 웹 페이지를 열람하는 사용자의 브라우저에서 실행되며, **사용자의 세션 쿠키, 개인 정보, 또는 웹 애플리케이션의 내용을 탈취하거나 조작**할 수 있다.

## ✅ CSRF 방어

- **CSRF 토큰 사용 :** 모든 중요한 요청에 고유한 CSRF 토큰을 포함시켜 사용자의 세션과 연결한다. 이렇게 하면 악의적인 웹 사이트에서 사용자의 브라우저를 통해 요청을 보내더라도 올바른 토큰이 없으면 요청이 거부된다.
  ![](https://velog.velcdn.com/images/sju4486/post/08af3b10-482b-447f-8cf3-f61c7115b44a/image.png)

- **SameSite 쿠키 속성 설정 :** 쿠키의 SameSite 속성을 Strict 또는 Lax로 설정하여 외부 사이트에서 요청을 보내는 것을 방지한다.

- **HTTP Referer 검증 :** HTTP Referer 헤더를 사용하여 요청이 원래 사이트에서 온 것인지 확인할 수 있다. 그러나 Referer 헤더는 신뢰성이 없을 수 있으므로 단독으로 사용하지 말아야 한다.

## ✅ XSS 방어

- **입력 값의 검증과 이스케이프 :** 모든 입력 값(사용자 입력, URL 매개변수, 쿠키 등)을 적절히 검증하고 이스케이프하여 웹 페이지에 삽입되지 않도록 한다. 이렇게 하면 악성 스크립트가 실행되지 않는다.

- **CORS (Cross-Origin Resource Sharing) 사용 :** 웹 페이지에서 외부 도메인의 리소스에 대한 접근을 제한하고 필요한 경우 CORS 정책을 사용하여 접근을 허용한다.

- **Content Security Policy (CSP) 설정 :** CSP 헤더를 사용하여 허용된 리소스 및 스크립트 출처를 명시적으로 지정하여 악성 스크립트의 실행을 방지한다.

- **브라우저에 내장된 XSS 필터 사용 :** 대부분의 현대 웹 브라우저는 기본적인 XSS 필터를 내장하고 있다. 이러한 필터를 활성화하고 사용하는 것이 좋다.

## 참고

- https://velog.io/@jupiter-j/CSRF%ED%86%A0%ED%81%B0%EC%9D%B4%EB%9E%80
- https://learn.microsoft.com/ko-kr/azure/active-directory/develop/howto-handle-samesite-cookie-changes-chrome-browser?tabs=dotnet
- https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Referer
- https://developer.mozilla.org/ko/docs/Web/HTTP/CORS
- https://developer.mozilla.org/ko/docs/Web/HTTP/CSP
