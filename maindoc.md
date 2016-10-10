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
3. [Atores Envolvidos]
4. [Funcionalidade do aplicativo](#funcionalidade-do-aplicativo)
5. [Código](#código)

## Este documento

## Introdução

## Atores Envolvidos

Por ser um projeto open source, Android Backup+ evoluiu muito ao longo doe tempo, graças a muitos atores envolvidos no projeto:

*Desenvolvedores: Consistem principalmente em membros da comunidade do GitHub, mas teoricamente, o código é aberto para que qualquer usuário com conta no GitHub (não necessariamente membro da comunidade) possa dar commits.
*Usuários: Consistem principalmente de usuários de celulares Android que desejam fazer backup de suas mensagens SMS. 
Consist mainly of highly advanced computer users like programmers and system administrators. Atom is also preferred by users when an IDE is not available or too much work to set up.
Maintainers: Atom is maintained by the core developers, but GitHub is the main driver in keeping the project alive. They make sure that there are enough developers for the Atom project and invest time and money in making sure the Atom project stays alive.
Support staff: Consists mainly of a lot of volunteers, but next to that also the GitHub staff and core developers. This is done by responding to issues, triaging issues and pull requests, closing bugs as duplicate or filed on the wrong repository, and much more. Also the Forum and Slack are used for quick support to the end users and developers. Lee Dohm is the main community manager and manages all supporting staff.
Testers: The main users test the system and report bugs to the issue tracker on GitHub. There is no special test team available although the core developers test most pull requests before merging.
Production Engineers: All tools like GitHub, the Forum, Slack and the build servers are maintained by the GitHub team. They make sure it is running and invest time in updates or setting up new tools.
Assessors: The core development team of Atom oversees the conformance of the programming standards. They check each pull request with multiple people and also check if it is still in line with the future planning.

## Funcionalidade do aplicativo

## Caso de uso

## Código
