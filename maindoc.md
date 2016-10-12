# Documentação de sms-backup-plus <h1>

![Logo do programa]
(https://lh3.googleusercontent.com/O5XiRSakINV9UQjXEsrV_cadlCX_D8vf2eO614jWYnY-JJoteOqxel1Hj8A_K578lPk=w300-rw)

#Table of Contents
1. [Este documento](#este-documento)
2. [Introdução](#introdução)
3. [Atores Envolvidos](#atores-envolvidos)
4. [Funcionalidade do aplicativo](#funcionalidade-do-aplicativo)
5. [Código](#código)

## Introdução

Essa aplicação é um fork da aplicação SMS Backup, cujo desenvolvimento parou há algum tempo. SMS-Backup-Plus utiliza Gmail para realizar backup de SMS, MMS e Log de ligações, através da rede.

Difereças / Melhorias:

* Nova funcionalidade de restauração. SMS armazenados no Gmail pode ser transferidos de volta para o telefone. Essa funcionalidade permite até que usuários que já tenham criado um backup com versões mais antigas do SMS Backup. Entretanto, MMS ainda não podem ser restaurados.

* SMS Backup+ nunca irá pedir pela senha do Gmail do usuário. SMS Backup+ utiliza XOAuth para ter acesso aos dados do usuário. Esse acesso pode ser revogado a qualquer momento.

* SMS Backup+ pode ser encontrado gratuitamente na Google Play Store. Não há (e o desenvolvedor garante que não irá) uma versão pro ou paga. 

## Este documento

## Atores Envolvidos

Por ser um projeto open source, Android Backup+ evoluiu muito ao longo doe tempo, graças a muitos atores envolvidos no projeto:

* Desenvolvedores: Consistem principalmente em membros da comunidade do GitHub, mas teoricamente, o código é aberto para que qualquer usuário com conta no GitHub (não necessariamente membro da comunidade) possa dar commits.

* Usuários: Consistem principalmente de usuários de celulares Android que desejam fazer backup de suas mensagens SMS. A página do App no Google Play conta com mais de 54 mil downloads e 4.4 estrelas. Os usuários não necessariamente possuem um conhecimento grande de computação ou Android para utilizar o Aplicativo.

* Mantenedores: SMS Backup+ é mantido pela equipe original de desenvolvedores, particularmente pelo usuário criador do projeto no GitHub, que também mantém o Aplicativo na Google Play. Além dessa equipe, diversos outros usuários no GitHub são responsáveis pela manutenção do código, como fica demonstrado pelo histórico de commits:

![alt test] (https://github.com/talesbarreto/Egenharia-Software2-TP1/blob/master/Captura%20de%20Tela%202016-10-10%20a%CC%80s%2015.37.39.png "Commits ao longo do tempo")

* Suporte: Consiste principalmente de voluntários, principalmente equipe do GitHub e os desenvolvedores da Equipe definida acima. Os erros podem ser inscritos no próprio GitHub, via "Issues". A própria comunidade do GitHUb se responsabiliza por resolver os problemas, analisando pull requests, fechando bugs, problemas no repositório, etc.

* Testers: Os usuários principais do sistema são responsáveis por reportar bugs através de "Issues" no GitHub. Não existe uma equipe de teste disponível, embora a equipe de desenvolvedores testa a maioria dos pull requestes antes de dar merge.


## Funcionalidade do aplicativo

## Caso de uso

## Código
### Principais frameworks, ferramentas e linguagens usadas no desenvolvimento.
### Arquitetura 
### Principais módulos
#### Activity
Código responsável pela lógica da interface gráfica, tratando eventos de input do usuário e convocando os métodos correspondentes de cada funcionalidade apresentada nas opções de cada tela, que são basicamente três:
<p>
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103446.png"  width="250"> 
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103533.png"  width="250"> 
<img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Screenshot_20161012-103554.png"  width="250"> 
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
<p><img src="https://github.com/talesbarreto/Engenharia-Software2-TP1/blob/master/prints_interface/Classe-defaults.png"> 
</p>

#### Receiver
Este código é responsável por escutar o evento do sistema relacionado ao recebimento de mensagens. Caso o usuário configure o aplicativo para fazer backups automáticos, o aplicativo tratará cada mensagem recebida de forma proativa, realizando o backup na conta de e-mail dele.

#### Service
Este é o código responsável por implementar o serviço do sistema. Diferentemente do comportamento de aplicativos normais, serviços não são encerrados pelo sistema operacional quando o usuário não está interagindo com o aplicativo. Dessa forma, o aplicativo pode agir em segundo plano realizando os backups sem o usuário precisar ser incomodado. 

#### tasks e utils
Estes dois módulos implementam códigos auxiliares, que não são interesses funcionais do aplicativo. Nele, há métodos relativo à co-rotinas e thread pool, por exemplo.
