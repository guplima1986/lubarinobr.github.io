---
layout: post
title: "Utilizando EditorConfig para padronização de editor"
description: "O começo de tudo."
tags: [editorConfig, programador,editor de texto,DevOps]
modified: 2017-07-25
comments: true
image:
  
---

<figure>
	<img src="{{ site.url }}/images/editorConfig.png" alt="Editor Config"/>
</figure>
Você muito provavelmente já teve problema com o encoded ou identação trabalhando em um projeto em equipe, cada programador tem sua IDE ou Editor de Texto com suas configurações preferidas e com isso os problemas surgem, caracteres quebrados, identação por espaço ao invés de tab , identação arquivos .alguma-coisa errada. Mas para isso existe solução e aqui vou mostrar como configurar o plugin do <a href="http://editorconfig.org/">editorConfig</a>  

## O que é EditorConfig

<blockquote>EditorConfig helps developers define and maintain consistent coding styles between different editors and IDEs.</blockquote>

Ele simplesmete é um arquivo .editorconfig que pode ser configurado com o estilo de codificação planejado pela equipe. Ele pode ser utilizado em diversos editores como por exemplo o Sublime, ATOM e IDE como o eclipse e NetBeans. Você pode conferir se o seu editor preferido oferece suporte ao editorConfig <a href="http://editorconfig.org"> aqui</a>.	

Aqui você pode ver um exemplo do arquivo de configuração minima.

<figure>
	<img src="{{ site.url }}/images/editorConfigFile.png" alt="Editor Config"/>
</figure>

Você pode provisionar o arquivo para que toda a sua equipe utilize o mesmo coding style independente da configuração do editor do desenvolvedor

## Instalando o editorConfig no eclipse

Para utilizar o editorConfig no seu eclipse basta instalar o plugin que pode ser encontrado no eclipse MarketPlace.

<img src="{{ site.url }}/images/editorConfigMarket.png" alt="Editor Config"/>

Ou no github do projeto <a href="https://github.com/ncjones/editorconfig-eclipse#readme">aqui</a>

<img src="{{ site.url }}/images/editorConfigGithub.png" alt="Editor Config"/>


## Utilizando o editorConfig

O charset que está sendo utilizado para esse tutorial será do LATIM1 para o UTF-8

<img src="{{ site.url }}/images/editorCharset.png" alt="Editor Config"/>

Para começamos a utilizar o editorConfig você precisar criar um arquivo .editorconfig no root do projeto, eu irei utilizar a configuração minima.


```java
root = true

[*]
end_of_line = lf
insert_final_newline = true

[*.{java,js}]
charset = "UTF-8"

[*.java]
indent_style = tab

[{pom.xml}]
indent_style = tab
indent_size = 2
```  

<h3>Explicação</h3>

```java
root = true

[*]
end_of_line = lf
insert_final_newline = true
```

Aqui informo que a configuração do editor será aplicado em todo o projeto  e que para todo fim de linha será adicionado uma nova linha.

```java
[*.{java,js}]
charset = "UTF-8"

[*.java]
indent_style = tab

[{pom.xml}]
indent_style = tab
indent_size = 2
```
Definimos a configuração do charset para os arquivos .java e .js e apenas a identação por tab para os arquivos .java.
Também defino uma configuração personalizada para o pom.xml


Basta você salvar o arquivo e todo o projeto estará configurado com o coding style definido no arquivo. Caso o editor não tenha sido configurado depois de ter salvo basta formatar o projeto novamente (CTRL + SHIFT + K) no root do projeto.

O editorConfig é uma ferramenta muito útil, principalmente como se trabalha em equipe a configuração também é bastante simples e personalizável onde você pode está implementado a medida das suas necessidades basta ver sua documentação.

Espero que isso ajude a todos vocês.