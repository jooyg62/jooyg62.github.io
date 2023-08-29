---
layout: default
title: Annotation
parent: Spring Framework
nav_order: 1
# has_children: true
---

# Annotation

`@SpringBootApplication` 이란?<br>
Application 이 실행되면 아래 `PetClinicApplication.java` 코드의 `main` 함수가 실행됩니다. 

그 전에 `@SpringBootApplication` 은 스프링부트를 자동으로 설정해주는 Annotation 입니다. 

Spring 에 설정된 Class 들을 읽고 필터링하여 자동으로 Bean 으로 등록합니다.

`SpringApplication.run()` 함수는 내장 WAS 를 사용하여 Application 을 실행시켜주기 때문에 Tomcat 을 따로 설치할 필요가 없고, SpringBoot 로 만들어진 jar 파일로 실행시켜 주면 됩니다.

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

---

