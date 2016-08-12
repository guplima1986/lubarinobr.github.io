---
layout: post
title: "Trabalhando com Reflections Parte I"
description: "Utilizando reflection para obter informações de atributos."
tags: [Reflection]
modified: 2017-08-12
comments: true
image:
  
---

<figure>
	<img src="{{ site.url }}/images/reflection.jpg" alt="Java Reflection"/>
</figure>

Bom pessoal, venho aqui falar um pouco sobre Reflection, mas antes de começamos irei especificar um pouco sobre o conceito da Reflecção.

<blockquote>Reflection é a capacidade de um programa se observar (Introspecção), podendo obter informações de si mesmo e modificar sua estrutura, o paradigma de reflexão pode também ajudar na melhoria do código </blockquote>


## Utilizando Reflection

Como de toda natureza de um programa o mesmo tende a crescer seja ela de forma planejada ou não, independente da forma que o mesmo cresce a gente se depara com uns métodos desse tipo.


```java

public class foo{

	public boolean existeNulos(Bar bar){

		if(bar.getId() == null){
			return true;
		}

		if(bar.getName() == null){
			return true;
		}

		if(bar.getAge() == null){
			return true;
		}

		if(bar.getAdress() == null){
			return true;
		}

		if(bar.getPhone() == null){
			return true;
		}

		if(bar.getCellPhone() == null){
			return true;
		}

		if(bar.getDocument() == null){
			return true;
		}

	} 

	return false;
}

```

Okay, também concordo que isso não é nenhuma grande método mas aposto que um dia ela poderá se tornar. O exemplo acima mostra que sempre que um novo atributo for adicionado na classe você vai ter que vim aqui e validar se o novo atributo é nulo.

Mas Como eu disse anteriomente, a Reflection tem uma característica que é de melhoria no código, seja ela de perfomace ou/e de refactory, então se eu fosse verificar se existe algum atributo nulo com Reflection eu simplesmente implementaria isso.

```java

public class foo{
	public boolean existeNulos(Object obj){
 		Class<?> clazz = obj.getClass();

		try {
			for(Field field : clazz.getDeclaredFields()){
				field.setAccessible(true);
				Object value = field.get(obj);
				if(value == null){
					return true;
				}
			}
		}catch (Exception e) {
			throw new RuntimeException("Erro ao ler campo");
		}

			return false;
		}
				
	}

```

Visivelmente meu código se tornou muito menos cansativo de ler e outro beneficio é que agora você pode validar qualquer atributo de qualquer objeto, evitando repetição de código.

## Entendo um pouco sobre o código

A primeiro coisa a ser feita é pegar a class do objeto passado por parâmetro

```java
	Class<?> clazz = obj.getClass();
```

Logo em seguida foi feito um forEach na lista de Atributos declarados utilizando o <b>getDeclaredFields()</b> que retornar todos atributos da classe. Caso você utilize o <b>getFields</b> só irá ser retornados os atributos públicos.

```java
try {
   for(Field field : clazz.getDeclaredFields()){
   ...
```

Para cada atributo eu o torno acessível para que eu possa acessar seu estado e em seguida crio um atributo do tipo <b>Object</b> que recebe o valor do atributo, verifico se o mesmo é nulo ou não.

```java
   field.setAccessible(true);
   Object value = field.get(obj);
   if(value == null){
      return true;
   }
```

## Resumidamente falando
Isso é apena o começo de uma serie de artigos que irei fazer sobre reflection abordando sobre como trabalhar com  class,fields, methods e annotation.

Até a próxima pessoal e não se esqueçam de deixar seu comentário com dúvidas ou críticas !

<h3>Referências</h3>
<a>https://docs.oracle.com/javase/tutorial/reflect/</a>