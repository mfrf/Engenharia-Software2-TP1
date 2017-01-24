# Documentação de sms-backup-plus<h1>

![Logo do programa]
(https://lh3.googleusercontent.com/O5XiRSakINV9UQjXEsrV_cadlCX_D8vf2eO614jWYnY-JJoteOqxel1Hj8A_K578lPk=w300-rw)

#Table of Contents

1. [Este documento](#este-documento)
2. [Introdução](#introdução)
3. [Atores Envolvidos](#atores-envolvidos)
4. [Funcionalidade do aplicativo](#funcionalidade-do-aplicativo)
5. [Código](#código)
6. [Conclusão](#conclusão)
7. [Referências](#referências)


## Este documento
Este documento é um trabalho da disciplina Engenharia de Software ll, do [Departamento de Ciências da Computação](http://dcc.ufmg.br/dcc/) da [UFMG](https://www.ufmg.br). A proposta deste trabalho é desenvolver uma documentação de algum projeto OpenSource presente nos repositórios do GitHub. A aplicação escolhida foi o [SMS backup Plus](https://github.com/jberkel/sms-backup-plus), um aplicativo de backup de mensagens de smartphones android.

## Introdução

Essa aplicação é um fork da aplicação SMS Backup, cujo desenvolvimento parou há algum tempo. SMS-Backup-Plus utiliza Gmail para realizar backup de SMS, MMS e Log de ligações, através da rede. O software pode ser encontrado para baixar no [Google Play](https://play.google.com/store/apps/details?id=com.zegoggles.smssync), a loja oficial da plataforma. O aplicativo possui suporte para as versões mais novas do sistema e ainda é relevante, já que o sistema da Google não oferece suporte para sincronia de mensagens SMS na nuvem.

A aplicabilidade de se usar tal tipo de aplicativo vem principalmente por usuários de versões de Android antigas, que ainda usam muito SMS e MMS, e precisam fazer backup de tais mensagens para caso percam ou precisem resetar o celular. O uso de SMS ainda é muito comum nos USA e em países da Europa.
A interface da aplicação não segue o Material Design da Google, o que sugere que é uma aplicação estável, que não precisa ou não quer evoluir. 

### Releases

#### Documentação das releases

Os lançamentos de novas versões do software têm pouquíssimas descrições do que foi feito em cada uma delas. Como o projeto começou pequeno, sob o trabalho de apenas um desenvolvedor, não houve preocupação em registrar o trabalho. Apenas na ultima release, a 1.5.10, houve um trabalho mais aprimorado de engenharia de software, com muitas releases betas e logs do que foi feito em cada uma. 

#### Ultima release 1.5.10
**Lançamento**: 20 de agosto de 2015
##### Novos recursos
* Novo ícone
* Integração com o  K9
* Suporte para o fluxo web do OAuth2
* Tradução para albanês
* Tradução para ucraniano
* Suporte para versões Android KitKat
* Suporte para versões Android Lollipop

##### Aperfeiçoamentos
* Suporte OAuth2 melhorado
* Removido suporte ao Whatsapp
* [Removido códigos do Whatsapp](https://github.com/jberkel/sms-backup-plus/issues/564)
* Compatibilidade para Android 2 melhorada

#### Correção de bugs
* [Consertado bug de notificação](https://github.com/jberkel/sms-backup-plus/issues/562)
* Consertado bug de atualização to token do OAuth2
* Consertado id de chamada desconhecida
* [Consertado codificação de binãria](https://github.com/jberkel/sms-backup-plus/issues/512)
* [SSL/TLS](https://github.com/jberkel/sms-backup-plus/issues/513)
* Parsing do nome de usuário

#### Releases anteriores

A tabela abaixo apresenta uma relação de todas as releases já lançadas. A coluna *Principal mudança* é uma descrição fornecida pelo autor do commit da release.

| Data de lançamento | Versão | Principal mudança|
|--------------------|:-------|:------------------|
| 2016-10-21 16:12:43 | 1.5.11-BETA3 | Merge pull request #686 from jberkel/upgrade-k9|
| 2015-10-07 10:16:49 | 1.5.11-BETA2 | Bump version code|
| 2015-09-20 12:59:15 | 1.5.11-BETA1 | Bump version|
| 2015-08-20 13:06:06 | 1.5.10-BETA1, tag: 1.5.10 | New app icons #580, prepare resubmission|
| 2015-06-23 17:43:08 | 1.5.9 						| Bump version|
| 2015-06-12 10:57:22 | 1.5.9-BETA6 | Asset for console|
| 2015-06-06 13:02:45 | 1.5.9-BETA5 | Log migration|
| 2015-06-04 20:03:56 | 1.5.9-BETA4 | Move everything to OAuth2, drop XOAuth|
| 2015-03-06 03:20:39 | 1.5.9-BETA3 | Log unknown call ids|
| 2015-01-12 22:12:38 | 1.5.9-BETA2 | Albanian translation updates|
| 2015-01-11 10:07:09 | 1.5.9-BETA1 | Update pom|
| 2015-01-09 01:29:59 | 1.5.8 | Bump version|
| 2014-12-31 00:09:08 | 1.5.8-BETA2 | 2.2 compat|
| 2014-12-30 15:37:03 | 1.5.8-BETA1 | Changes|
| 2014-12-29 23:46:21 | 1.5.7 | Update changes|
| 2014-12-28 10:29:43 | 1.5.7-BETA2 | Changes|
| 2014-12-28 02:52:46 | 1.5.7-BETA1 | changes|
| 2014-12-24 19:35:24 | 1.5.6-DEBUG | Enable debug|
| 2014-12-21 15:28:09 | 1.5.6 | Changes|
| 2014-12-19 15:39:13 | 1.5.6-RC1 | Bump again|
| 2014-12-19 13:11:49 | 1.5.6-BETA11 | Fix tests|
| 2014-12-17 02:21:11 | 1.5.6-BETA10 | Debug|
| 2014-12-15 19:02:58 | 1.5.6-BETA9, tag: 1.5.6-BETA8 | Use new version of k9-mail|
| 2014-12-11 17:58:51 | 1.5.6-BETA7 | Bump imapstore|
| 2014-11-21 15:51:56 | 1.5.6-BETA6 | Changes|
| 2014-11-21 15:00:51 | 1.5.6-BETA5 | Bump version|
| 2014-11-18 15:29:32 | 1.5.6-BETA4 | Bump version|
| 2014-11-18 12:36:52 | 1.5.6-BETA3 | Use new build tools|
| 2014-11-17 01:16:54 | 1.5.6-BETA2 | New launcher icons|
| 2014-11-14 18:33:19 | 1.5.6-BETA1 | Don't unregister in onDestroy|
| 2013-07-16 00:31:38 | 1.5.5 | changes|
| 2013-07-11 02:46:25 | 1.5.5-BETA2 | Bump version|
| 2013-07-10 23:03:01 | 1.5.5-BETA1 | Updated about|
| 2013-07-09 01:28:15 | 1.5.4 | typo|
| 2013-07-09 01:01:08 | 1.5.4-BETA2 | Fix contact group selection|
| 2013-07-07 16:39:43 | 1.5.4-BETA1 | Added nullable annotation|
| 2013-07-02 00:18:28 | 1.5.3 | Prepare release|
| 2013-06-09 05:33:28 | 1.5.2 | CHANGES|
| 2013-06-07 15:21:37 | 1.5.1 | Bump version|
| 2013-06-07 00:08:15 | 1.5.0 | Bump|
| 2013-01-18 20:44:27 | 1.4.8 | Prepare 1.4.8|
| 2013-01-12 21:06:21 | 1.4.7 | Fall back to browser based auth if there are no accounts|
| 2012-09-06 17:25:04 | 1.4.6 | **Indisponível**|
| 2012-01-02 21:31:37 | 1.4.5 | **Indisponível**|
| 2011-11-26 14:51:44 | 1.4.4 | **Indisponível**|
| 2011-02-08 13:34:43 | 1.4.3 | **Indisponível**|
| 2011-02-08 01:40:15 | 1.4.2 | **Indisponível**|
| 2011-01-29 00:59:15 | 1.4.1 | **Indisponível**|
| 2011-01-13 03:02:45 | 1.4.0 | **Indisponível**|
| 2010-12-22 01:38:02 | 1.3.7 | **Indisponível**|
| 2010-12-22 01:04:25 | 1.3.6 | **Indisponível**|
| 2010-12-19 22:22:04 | 1.3.5 | **Indisponível**|
| 2010-12-10 00:41:00 | 1.3.4 | **Indisponível**|
| 2010-12-02 01:55:38 | 1.3.3 | **Indisponível**|
| 2010-11-30 22:20:31 | 1.3.2 | **Indisponível**|
| 2010-11-30 15:02:17 | 1.3.1 | Null guard|
| 2010-11-30 02:12:22 | 1.3 | **Indisponível**|
| 2010-11-10 20:32:41 | 1.2 | **Indisponível**|
| 2010-11-04 13:57:08 | 1.1.5 | **Indisponível**|
| 2010-10-26 20:58:19 | 1.1.4 | **Indisponível**|
| 2010-10-23 18:24:53 | 1.1.3 | **Indisponível**|
| 2010-10-23 17:34:48 | 1.1.2 | fix npe|
| 2010-10-14 15:43:40 | 1.1.1 | **Indisponível**|
| 2010-10-13 00:21:46 | 1.1 | **Indisponível**|
| 2010-10-05 23:13:56 | 1.0.11 | **Indisponível**|
| 2010-09-30 03:43:48 | 1.0.10 | **Indisponível**|
| 2010-09-25 05:13:52 | 1.0.9 | **Indisponível**|
| 2010-09-17 00:40:03 | 1.0.8 | **Indisponível**|
| 2010-09-10 19:55:17 | 1.0.7 | **Indisponível**|
| 2010-09-07 22:44:05 | 1.0.6 | **Indisponível**|
| 2010-08-19 09:36:22 | 1.0.5 | **Indisponível**|
| 2010-08-17 11:26:18 | 1.0.4 | **Indisponível**|
| 2010-08-15 16:20:37 | 1.0.3 | **Indisponível**|
| 2010-08-14 20:34:32 | 1.0.2 | **Indisponível**|
| 2010-08-10 20:40:48 | 1.0.1 | **Indisponível**|
| 2010-08-08 23:35:31 | 1.0 | **Lançamento**|


###Principais difereças e Melhorias anunciadas na ultima versão:

* Nova funcionalidade de restauração. SMS armazenados no Gmail pode ser transferidos de volta para o telefone. Essa funcionalidade permite até que usuários que já tenham criado um backup com versões mais antigas do SMS Backup migrem para a nova funcionalidade sem problemas. Entretanto, MMS de versões antigas ainda não podem ser restaurados.

* SMS Backup+ nunca irá pedir pela senha do Gmail do usuário. SMS Backup+ utiliza XOAuth para ter acesso aos dados do usuário. Esse acesso pode ser revogado a qualquer momento.

* Suporte para Backup de MMS (desde a versão `1.1`), disponível apenas para Android 2.x

* Backup de Log de ligações (desde a versão `1.2`), com integração com Google Calendário (desde a versão `1.3.`) e restauração (desde `1.4`).

* Batch size limits removed.

* Funciona com qualquer servidor IMAP (mas com Gmail como default).

Testado com Android 2.x - 6.0.x.

* SMS Backup+ pode ser encontrado gratuitamente na Google Play Store. Não há (e o desenvolvedor garante que não irá) uma versão pro ou paga. 

## Atores Envolvidos

Por ser um projeto open source, Android Backup+ evoluiu muito ao longo doe tempo, graças a diversos atores envolvidos no projeto:

* Desenvolvedores: Consistem principalmente em membros da comunidade do GitHub, mas teoricamente, o código é aberto para que qualquer usuário com conta no GitHub (não necessariamente membro da comunidade) possa dar commits.Os principais Desenvolvedores são:

+ [jberkel](https://github.com/jberkel) -> é o dono do repositório, e consequentemente o que mais contribui, sendo responsável por quase 1100 commits no código.
+ [marcher233](https://github.com/marcher233) -> segundo em contribuição, mas com apenas 10 commits. Provavelmente é um membro da comunidade GitHub do APP.

* Usuários: Consistem principalmente de usuários de celulares Android que desejam fazer backup de suas mensagens SMS. A página do App no Google Play conta com mais de 50 milhões de instalações e 4.4 estrelas, avaliado por  56,206 usuários. Os usuários não necessariamente possuem um conhecimento grande de computação ou Android para utilizar o Aplicativo. Abaixo um snapshot da página do aplicativo no Google Drive, com as informações de uso:
![imagem1](https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/analiseSMSBackup.png?raw=true "Dados GooglePlay")

* Mantenedores: SMS Backup+ não possui uma equipe de desenvolvedores ou de mantenedores por si, o que há é o Desenvolvedor da aplicação jberkel, que a mantém tanto no GitHub quanto na GooglePlay. Entretanto, por ser Open Source, a aplicação conta com diversos colaboradores (40 no total até o momento) no GitHub, que se preocupam com resolver as Issues e alterar partes do código que possam estar defeituosas. Mas todos os pull requests passam pelo crivo do Desenvolvedor. Abaixo um snapshot do histórico de commits da aplicação:

![imagem2] (https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/Captura%20de%20Tela%202016-10-10%20a%CC%80s%2015.37.39.png?raw=true "Commits ao longo do tempo")

* Suporte: Consiste principalmente de voluntários, principalmente equipe do GitHub e os desenvolvedores da Equipe definida acima. Os erros podem ser inscritos no próprio GitHub, via "Issues". A própria comunidade do GitHUb se responsabiliza por resolver os problemas, analisando pull requests, fechando bugs, problemas no repositório, etc.

* Testers: Os usuários principais do sistema são responsáveis por reportar bugs através de "Issues" no GitHub. Não existe uma equipe de teste disponível, embora a equipe de desenvolvedores testa a maioria dos pull requestes antes de dar merge.

## Código

O código é escrito nos padrões de projetos Android. A linguagem Java é a usada para o desenvolvimento da parte lógica, enquanto a interface gráfica é descrita em linguagem XML:
 <p><img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/XML_interface.png?raw=true"> 
 </p>
 O código usa as APIs e pacotes providos pelo Google para criação de aplicativos Android. Tipicamente, o desenvolvimento desse tipo de software é realizado em IDEs especializadas que pode ser uma versão modificada da [IDE Eclipse](https://www.eclipse.org/downloads/packages/eclipse-android-developers/neonm6) ou o [Android Studio](https://developer.android.com/studio/index.html), que pode ser visto na imagem acima.

### Principais frameworks e bibliotecas externas

#### Otto

[Otto](http://square.github.io/otto/) oferece um barramento simplificado para a plicação. Com ele, é possível realizar comunicação direta entre diferentes componentes. Com registradores e listeners, Otto implementa, por padrão, troca de mensagens assíncronas sem a necessidade de espera ocupada.

O código é muito simples. Para utiliza-lo, basta instanciá-lo:
```java
Bus bus = new Bus();
```
Cria um listener para receber mensagens:

```java
@Produce public AnswerAvailableEvent produceAnswer() {
    // Assuming 'lastAnswer' exists.
    return new AnswerAvailableEvent(this.lastAnswer);
}
```
Enviar mensagens:
```java
bus.post(new AnswerAvailableEvent(42));
```

Otto está sob a [licença Apache](http://www.apache.org/licenses/LICENSE-2.0) e o código fonte pode ser encontrado no [Github](https://github.com/square/otto).


#### Pay-me

Pay-me é uma biblioteca para Android com a finalidade de oferecer códigos bem testados e estabelecidos na comunidade para prover uma forma segura e padronizada do usuário oferecer doações para o desenvolvedor. 
O código está disponível no [Github](https://github.com/jberkel/pay-me) sob a [licença Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

#### JSON-Java


[JSON-Java](https://github.com/stleary/JSON-java) é uma biblioteca que permite a implementação e interpretação de códigos JSON, XML. HTTP, Cookies  e CDL em Java. A biblioteca é usada para estruturar e ler o banco de dados de backups.
O código está disponível no [Github](https://github.com/stleary/JSON-java) 

#### Signpost

O Signpost é a solução fácil e intuitiva para assinar mensagens HTTP na plataforma Java de acordo com o padrão   OAuth Core 1.0a. O Signpost segue um design modular e flexível, permitindo combiná-lo com diferentes camadas de mensagens HTTP. 

O padrão [OAuth Core 1.0a](https://oauth.net/core/1.0a/) permite que o usuário se autentique em serviços externos ao aplicativo para que este use seus recursos. A biblioteca é usada para que o aplicativo armazene as informações de backup na conta de e-mail do usuário.

#### jetbrains.annotations.Nullable

Esta biblioteca é usada para prover uma gerencia de exceções de acessos nulos, muitas vezes tratando alguns automaticamente. A biblioteca foi criada por [JetBrains](https://www.jetbrains.com/help/idea/2016.2/nullable-and-notnull-annotations.html) e sua documentação pode ser acessada no [site da empresa](https://www.jetbrains.com/help/idea/2016.3/nullable-and-notnull-annotations.html).


### Arquitetura

A aplicação é toda desenvolvida em Java, utilizando a tecnologia de Gerenciamento de Builds Apache Maven. Por seguir o Maven, a aplicação é estruturada em módulos bem definidos. A Arquietura do projeto adota a lógica arquitetural Apache Maven: aplicação dividida em módulos e submódulos organizados pela lógica de diretórios parents e childrens.

![imagem3](https://raw.githubusercontent.com/talesbarreto/Engenharia-Software2-TP1/master/prints_interface/maven-1-249x300.png "Exemplo arquietura Maven")
Exemplo de como uma Arquitetura Apache Maven se estrutura

Cada módulo controla alguma funcionalidade ou recurso da aplicação. O código fonte é separado dos recursos bem como os testes são separados de ambos. O build é realizado por um POM "Project Object Model", uma representação xml do projeto Maven, contendo todos os módulos, recursos, plugins e passos para executar o build.

####Sobre Arquitetura Maven

O Maven utiliza um arquivo XML (POM) para descrever o projeto de software sendo construído, suas dependências sobre módulos e componentes externos, a ordem de compilação, diretórios e plug-ins necessários. Ele vem com objetivos pré-definidos para realizar certas tarefas bem definidas como compilação de código e seu empacotamento.

O Maven baixa bibliotecas Java e seus plug-ins dinamicamente de um ou mais repositórios, como o Maven 2 Central Repository, e armazena-os em uma área de cache local.[2] Este cache local de artefatos baixados pode também ser atualizado com artefatos criados por projetos locais. Repositórios públicos podem também ser atualizados.

O Maven é construído utilizando uma arquitetura baseada em plugin, que permite que ele faça uso de qualquer aplicação controlável através da entrada padrão. Teoricamente, isto permitiria qualquer um escrever plugins para fazer interface com ferramentas de construção (compiladores, ferramentas de teste de unidade, etc.) para qualquer outra linguagem. De fato, o suporte e uso para linguagens diferentes de Java tem sido mínimas. Atualmente existe um plugin para o framework .NET e é mantido, e um plugin nativo C/C++ é mantido para o Maven 2.

### Principais módulos


<p>
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/cloves_arquitetura/prints_interface/uml.png?raw=true">
</p>

Estrutura sequencial dos módulos.

Os códigos são modularizados em pastas, nomeadas de acordo com suas funcionalidades implementadas. Apesar de todo o código estar inserido em apenas um pacote Java, a organização do diretório permite um bom entendimento a primeira vista. As principais pastas e suas breves descrições são descritas a seguir

<p>
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/EstruturaSMSBakcup.png?raw=true">
</p>

Estrutura de pastas do código fonte.

#### Activity
Código responsável pela lógica da interface gráfica, tratando eventos de input do usuário e convocando os métodos correspondentes de cada funcionalidade apresentada nas opções de cada tela, que são basicamente três:
<p>
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103446.png?raw=true"  width="250"> 
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103533.png?raw=true"  width="250"> 
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103554.png?raw=true"  width="250"> 
</p>
A interface gráfica do aplicativo não é sofisticada, já que sua funcionalidade não é interativa. Apenas há recursos de backup sob demanda e configurações de backups automáticos.

#### Auth
Este módulo é responsável por prover a autenticação do usuário com sua conta de e-mail do [Gmail](https://www.google.com/intl/pt-BR/mail/help/about.html). Este módulo usa o recurso [OAuth2UserAgent](https://developers.google.com/identity/protocols/OAuth2UserAgent) da API do Google, que permite que o usuário use a autenticação já realizada do usuário com o sistema operacional para se autenticar no serviço do Gmail através do aplicativo, requisitando apenas a permissão do usuário.
Esta estratégia é muito importante para elevar a segurança do usuário, já que ele não precisará digitar sua senha no aplicativo. Toda a tarefa de autenticação é delegada ao sistema.

#### Calendar
O código deste módulo permite a integração do backup com o [Google Calendar](https://www.google.com/calendar/about/). As informações como data e hora são adicionadas como acontecimentos no calendário do usuário. Desta forma, ele poderá buscar uma mensagem fazendo uma busca por tempo.

#### Contacts
A funcionalidade provida por este módulo é obter o usuário da mensagem, através da lista de contatos do usuário. Dessa forma, ao buscar uma mensagem no sistema de backup, o usuário poderá procurar pelo nome do contato e não precisará lidar com o número telefônico dele.

#### Mail
Este é um dos módulos mais importantes do programa. Ele acessa a conta de e-mail do usuário e armazena lá as todas as mensagens para backup. Neste módulo também há classes auxiliares que lidam com formatação e conversão de texto e tipo de dados. Além disso há códigos para uso de finalidades de e-mail como anexo de arquivo, por exemplo, para a criação do armzenamento em si.

#### Preferences
Este é o código responsável pela lógica da gerencia de configurações disponibilizadas para o usuário, através da interface gráfica do sistema. Cada configuração pertence à uma classe distinta e há uma classe específica para definir as configurações padrões do sistema:
<p><img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Classe-defaults.png?raw=true"> 
</p>

#### Receiver
Este código é responsável por escutar o evento do sistema relacionado ao recebimento de mensagens. Caso o usuário configure o aplicativo para fazer backups automáticos, o aplicativo tratará cada mensagem recebida de forma proativa, realizando o backup na conta de e-mail dele.

#### Service
Este é o código responsável por implementar o serviço do sistema. Diferentemente do comportamento de aplicativos normais, serviços não são encerrados pelo sistema operacional quando o usuário não está interagindo com o aplicativo. Dessa forma, o aplicativo pode agir em segundo plano realizando os backups sem o usuário precisar ser incomodado. 

#### tasks e utils
Estes dois módulos implementam códigos auxiliares, que não são interesses funcionais do aplicativo. Nele, há métodos relativo à co-rotinas e thread pool, por exemplo.

## Conclusão
O SMS Backup Plus, apesar de ser um fork de outra aplicação semelhante, possuí características de projeto bem interessantes. 

Primeiramente devemos notar o fato sobre o desenvolvimento ser realizado por poucas pessoas e, a grande maioria dos commits serem realizados pelo mesmo usuário. Isso mostra como este sistema, por mais que seja popular, não atraí muitos entusiastas para seu desenvolvimento. Cremos que isso se deve a própria arquitetura do sistema que não agrada aos desenvolvedores ou o próprio objetivo do sistema não mostra relevância para os mesmos. 

A arquitetura do sistema está bem definida. Vimos como as interfaces gráficas foram definidas através de XML e a estrutura lógica em Java. Além, citamos a utilização de tecnologia de Gerenciamento de Builds Apache Maven que permitiu que os módulos controlassem apenas a sua própria funcionalidade.

Vimos, também, a modularização do sistema que está bem independente entre si. Isso ajudou com a própria compreensão do sistema. 

Concluímos que, apesar de ser um sistema relativamente pequeno, o mesmo possuí uma estrutura arquitetural muito bem definida e robusta. Isto, certamente irá ajudar em casos de expansão bruta do sistema.

## Referências

1. jberkel/sms-backup-plus: Backup Android SMS, MMS and call log to Gmail / Gcal / IMAP - [https://github.com/jberkel/sms-backup-plus](https://github.com/jberkel/sms-backup-plus) - Acesso em Outubro de 2016.

2. Maven – Apache Maven IDE Integration - [https://maven.apache.org/ide.html](https://maven.apache.org/ide.html) - Acesso em Outubro de 2016.

3. Maven – Introduction to the POM - [https://maven.apache.org/guides/introduction/introduction-to-the-pom.html](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html) - Acesso em Outubro de 2016.

4. Using OAuth 2.0 for Client-side Web Applications &nbsp;|&nbsp; Google Identity Platform &nbsp;|&nbsp; Google Developers - [https://developers.google.com/identity/protocols/OAuth2UserAgent](https://developers.google.com/identity/protocols/OAuth2UserAgent) - Acesso em Outubro de 2016.
