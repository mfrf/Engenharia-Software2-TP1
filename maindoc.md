# Documentação de sms-backup-plus <h1>
![Logo do programa]
(https://lh3.googleusercontent.com/O5XiRSakINV9UQjXEsrV_cadlCX_D8vf2eO614jWYnY-JJoteOqxel1Hj8A_K578lPk=w300-rw)

Essa aplicação é um fork da aplicação SMS Backup, cujo desenvolvimento parou há algum tempo. SMS-Backup-Plus utiliza Gmail para realizar backup de SMS, MMS e Log de ligações, através da rede.

Difereças / Melhorias:

Nova funcionalidade de restauração. SMS armazenados no Gmail pode ser transferidos de volta para o telefone. Essa funcionalidade funciona até para usuário5s que já tenham criado um backup com versões mais antigas do SMS Backup. Entretanto, MMS ainda não podem ser restaurados.

SMS Backup+ nunca irá pedir pela senha do Gmail do usuário. SMS Backup+ utiliza XOAuth para ter acesso aos dados do usuário. Esse acesso pode ser revogado a qualquer momento.

SMS Backup+ pode ser encontrado gratuitamente na Google Play Store. Não há (e o desenvolvedor garante que não irá) uma versão pro ou paga. 

#Table of Contents
1. [Este documento](#este-documento)
2. [Introdução](#introdução)
3. [Atores Envolvidos](#atores-envolvidos)
4. [Funcionalidade do aplicativo](#funcionalidade-do-aplicativo)
5. [Código](#código)

## Este documento

## Introdução

## Atores Envolvidos

Por ser um projeto open source, Android Backup+ evoluiu muito ao longo doe tempo, graças a muitos atores envolvidos no projeto:

* Desenvolvedores: Consistem principalmente em membros da comunidade do GitHub, mas teoricamente, o código é aberto para que qualquer usuário com conta no GitHub (não necessariamente membro da comunidade) possa dar commits.

* Usuários: Consistem principalmente de usuários de celulares Android que desejam fazer backup de suas mensagens SMS. A página do App no Google Play conta com mais de 54 mil downloads e 4.4 estrelas. Os usuários não necessariamente possuem um conhecimento grande de computação ou Android para utilizar o Aplicativo.

* Mantenedores: SMS Backup+ é mantido pela equipe original de desenvolvedores, particularmente pelo usuário criador do projeto no GitHub, que também mantém o Aplicativo na Google Play. Além dessa equipe, diversos outros usuários no GitHub são responsáveis pela manutenção do código, como fica demonstrado pelo histórico de commits:

![alt test] (https://github.com/talesbarreto/Egenharia-Software2-TP1/blob/master/Captura%20de%20Tela%202016-10-10%20a%CC%80s%2015.37.39.png "Commits ao longo do tempo")

* Suporte: Consiste principalmente de voluntários, principalmente equipe do GitHub e os desenvolvedores da Equipe definida acima. Os erros podem ser inscritos no próprio GitHub, via "Issues". A própria comunidade do GitHUb se responsabiliza por resolver os problemas, analisando pull requests, fechando bugs, problemas no repositório, etc.

* Testeres: Os usuários principais do sistema são responsáveis por reportar bugs através de "Issues" no GitHub. Não existe uma equipe de teste disponível, embora a equipe de desenvolvedores testa a maioria dos pull requestes antes de dar merge.


## Funcionalidade do aplicativo

## Caso de uso

## Código
