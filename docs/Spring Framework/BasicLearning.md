---
layout: default
title: Basic Learning
parent: Spring Framework
nav_order: 1
# has_children: true
---

# Basic Learning

`@SpringBootApplication` 이란?<br>
Application 이 실행되면 아래 `PetClinicApplication.java` 코드의 `main` 함수가 실행된다. 

그 전에 `@SpringBootApplication` 은 스프링부트를 자동으로 설정해주는 Annotation 이다. 

Spring 에 설정된 Class 들을 읽고 필터링하여 자동으로 Bean 으로 등록한다.

`SpringApplication.run()` 함수는 내장 WAS 를 사용하여 Application 을 실행시켜주기 때문에 Tomcat 을 따로 설치할 필요가 없고, SpringBoot 로 만들어진 jar 파일로 실행시켜 주면 Application을 띄울 수 있다.

```java
// PetClinicApplication.java
package org.springframework.samples.petclinic;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.ImportRuntimeHints;

/**
 * PetClinic Spring Boot Application.
 */
@SpringBootApplication
@ImportRuntimeHints(PetClinicRuntimeHints.class)
public class PetClinicApplication {

	public static void main(String[] args) {
		SpringApplication.run(PetClinicApplication.class, args);
	}

}
```

`@ImportRuntimeHints` 은 무엇일까? `Spring Native Project` 와 관련있는 Annotation 으로 `GraalVM` 을 이용하여 `Native Image` 로 컴파일을 돕는 도구이다.
거의 사용할 일은 없다하니, 나중에 필요할 때 깊이 알아보는게 좋을 것 같다.

{: .note}
> Native 의 뜻은 특정 하드웨어 또는 플랫폼에 종속되어 실행되는 프로그램을 의미한다. 대표적인 예로 React Native 가 있고, React 를 사용하여 모바일 디바이스 앱을 개발할때 사용하는 프레임워크이다. 

---
`@Controller` 는 class 위에 작성하며, 이 클래스는 Controller 라는 의미이다.

`@GetMapping` 은 자원 접근 경로와 함께 function 위에 작성하며 접근 시 해당 func 로직을 수행한다.

리턴하는 문자열 값은 html 템플릿 경로가 담겨있는데, 해당 템플릿을 리턴된 데이터와 함께 결합하여 client 에 렌더링되는 html 페이지로 만들어준다.

- 어떻게 templates 하위 경로에 위치한 html 을 찾을 수 있었을까? 
- .html 을 붙이지 않고 어떻게 원하는 파일을 찾을 수 있었을까?

`resources/templates` 경로는 `Thymeleaf` 와 같은 템플릿 엔진을 사용할 때 default 경로이고, `.html` 로 끝나지 않아도 자동으로 인식을 한다.

```
main
|-- java
|-- resources
	|-- templates
		|-- owners
			|--createOrUpdateOwnerForm
```

```
...
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
...

@Controller
class OwnerController {
	...
	private static final String VIEWS_OWNER_CREATE_OR_UPDATE_FORM = "owners/createOrUpdateOwnerForm";
	...

	@GetMapping("/owners/new")
	public String initCreationForm(Map<String, Object> model) {
		Owner owner = new Owner();
		model.put("owner", owner);
		return VIEWS_OWNER_CREATE_OR_UPDATE_FORM;
	}
	...
}

```

---