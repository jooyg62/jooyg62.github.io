---
layout: default
title: Concept
parent: Spring Framework
nav_order: 2
# has_children: true
---

# Concept

## IoC(Inversion of Control) 란? 
한글로 번역하면 `제어의 역전` 이라는 뜻으로 풀이된다. 즉, 제어권이 나에게 있지 않고 상대로 뒤바껴있다는 뜻이다.
예를 들어, 클라이언트가 서버에게 요청을 보내면, Spring Framework 가 내부적으로 요청한 자원 경로에 해당하는 함수를 알아서 실행해주고, 아래 코드처럼 ownerId 값을 메소드의 인자로
넣어준 적이 없지만 Framework 에서 알아서 인자를 넣고 호출하여 준다. 또한, return 으로 html 파일명만을 적어줬을 뿐인데 Client 에 렌더링된 해당 html 을 전달해준다.

```
@GetMapping("/owners/{ownerId}/edit")
	public String initUpdateOwnerForm(@PathVariable("ownerId") int ownerId, Model model) {
		Owner owner = this.owners.findById(ownerId);
		model.addAttribute(owner);
		return VIEWS_OWNER_CREATE_OR_UPDATE_FORM;
	}
```

`프레임워크`와 `라이브러리` 이 둘의 차이점도 여기에 있다. 내가 직접 해당 코드를 실행시켜 흐름을 제어한다면 이건 `라이브러리`이지만 `프레임워크`는 내가 직접 호출을 수행하는 코드가 없고,
알아서 객체를 생성하고, 생명주기를 통제한다.

Spring Framework 를 `IoC 컨테이너`라고 얘기하는데 여기서 컨테이너의 뜻은 빈(Bean) 을 관리하고 의존성을 처리하는 컴포넌트를 얘기한다. 스프링에서 빈(Bean) 그리고 의존성 처리를 사용자가 직접하지 않기 때문에 `IoC 컨테이너`라고 불리는 것 같다.

스프링 컨테이너에는 두 가지 유형으로 분류할 수 있는데 `빈 팩토리(BeanFactory)` 와 `어플리케이션컨텍스트(ApplicationContext)` 가 있다. `빈 팩토리(BeanFactory)`는 딱 필요한 시점에만 빈(Bean) 을 생성하여 사용하기 때문에 효율적으로 자원을 사용한다. 실제로는 개발할 때 `어플리케이션컨텍스트(ApplicationContext)` 를 사용한다. `어플리케이션컨텍스트(ApplicationContext)`는 필요한 시점이 아닌 미리 빈(Bean) 을 생성해둔다. 그 외에도 다양한 기능을 처리해 준다. `AOP(Aspect-Oriented Programming)`, 이벤트 처리 등 많이 있지만 이것은 차차 알아가보려고 한다.

## POJO(Plain Old Java Object)란?



## IoC의 분류
Dl(Dependency Lookup)과 DI(Dependency Injection)


