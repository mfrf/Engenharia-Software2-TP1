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

Essa aplicação é um fork da aplicação SMS Backup, cujo desenvolvimento parou há algum tempo. SMS-Backup-Plus utiliza Gmail para realizar backup de SMS, MMS e Log de ligações, através da rede. O software pode ser encontrado para baixar no [Google Play](https://play.google.com/store/apps/details?id=com.zegoggles.smssync), a loja oficial da plataforma. O aplicativo possui suporte para as versões mais nova do sistema e ainda é relevante, já que o sistema da Google não oferece suporte para sincronia de mensagens SMS na nuvem.

Essa aplicação é um fork da aplicação SMS Backup, cujo desenvolvimento parou há algum tempo. SMS-Backup-Plus utiliza Gmail para realizar backup de SMS, MMS e Log de ligações, através da rede.

###Principais difereças e Melhorias:

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

* Mantenedores: SMS Backup+ não possui uma equipe de desenvolvedores ou de mantenedores per si, o que há é o Desenvolvedor da aplicação jberkel, que a mantém tanto no GitHub quanto na GooglePlay. Entretanto, por ser Open Source, a aplicação conta com diversos colaboradores (40 no total até o momento) no GitHub, que se preocupam com resolver as Issues e alterar partes do código que possam estar defeituosas. Mas todos os pull requests passam pelo crivo do Desenvolvedor. Abaixo um snapshot do histórico de commits da aplicação:

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
