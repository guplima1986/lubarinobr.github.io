---
layout: post
title: "Configurando proxy no eclipse"
description: "Configurando proxy no eclipse para acessar o marketplace ou qualquer conexão externa."
tags: [eclipse, proxy,proxy eclipse, ide]
modified: 2017-07-28
comments: true
image:
  
---

<figure>
	<img src="{{ site.url }}/images/eclipse-logo.png" alt="Editor Config"/>
</figure>
Algumas vezes você precisa utilizar o Marketplace para baixar um plugin para melhorar a usabilidade da sua IDE, Performace da sua aplicação ou qualquer outra coisa, mas muitas vezes você esbarra no problema de proxy da sua empresa ou até mesmo de casa e fica impossibilitado de baixar esses plugins, mas para isso existe solução e é bem simples.

## Configurando o proxy

Eu estou utilizando o <b>Eclipse Neon</b> mas acredito que não seja diferente para outras 
versões anteriores.

Vá até: <b>Window/Preferences/General/Network Connection</b>

<figure>
	<img src="{{ site.url }}/images/network-connection.png" alt="Janela Preference, aba Network connection"/>
</figure>

1° Na combobox do <b>Action Provider</b> selecione a opção Manual<br/>
2° Selecione HTTP e depois Edit<br/>
3° Insira sua configuração de proxy e pronto<br/>

<figure>
	<img src="{{ site.url }}/images/proxy-config.png" alt="Configuração do proxy"/>
</figure>

Agora você pode acessar o Marketplace e começar a baixar seus plugins.<br/>
Tenha um bom proveito.