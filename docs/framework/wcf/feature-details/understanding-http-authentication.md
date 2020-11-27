---
title: Fonctionnement de l'authentification HTTP
description: Consultez cette présentation de l’authentification HTTP dans WCF, y compris les schémas d’authentification HTTP et le choix d’un schéma d’authentification.
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: 65ccde358f4eb8727e59ca32fb9782b87e29c5c1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293518"
---
# <a name="understanding-http-authentication"></a>Fonctionnement de l'authentification HTTP

L'authentification est le processus visant à identifier si un client est susceptible d'accéder à une ressource. Le protocole HTTP prend en charge des authentifications dans le but de négocier l'accès à une ressource sécurisée.  
  
 La demande initiale d'un client est en général une demande anonyme, ne contenant aucune information d'authentification. Les applications serveur HTTP peuvent refuser la demande anonyme en indiquant qu'une authentification est requise. L'application serveur envoie des en-têtes WWW-Authenticate pour indiquer les schémas d'authentification pris en charge. Ce document décrit plusieurs schémas d’authentification pour HTTP et traite de leur prise en charge dans Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Schémas d'authentification HTTP  

 Le serveur peut spécifier plusieurs schémas d'authentification pour que le client en choisisse un. Le tableau ci-dessous décrit quelques-uns des schémas d'authentification couramment utilisés dans les applications Windows.  
  
|Schéma d'authentification|Description|  
|---------------------------|-----------------|  
|Anonyme|Une demande anonyme ne contient aucune information d'authentification. Cela équivaut à accorder à chacun l'accès à la ressource.|  
|De base|L'authentification de base envoie une chaîne encodée en Base64 qui contient un nom d'utilisateur et un mot de passe pour le client. Le mode Base64 n'est pas un type de chiffrement et sont utilisation doit être considérée comme l'envoi du nom d'utilisateur et du mot de passe en texte clair. Si une ressource doit être protégée, envisagez d'utiliser un schéma d'authentification autre que l'authentification de base.|  
|Digest|L’authentification Digest est un schéma de type stimulation/réponse destiné à remplacer l’authentification de base. Le serveur envoie une chaîne de données aléatoires appelée *nonce* au client en tant que défi. Le client répond avec un hachage qui inclut le nom d'utilisateur, le mot de passe et la valeur à usage unique entre autres informations. La complexité que cet échange introduit et le hachage des données compliquent le vol et la réutilisation des informations d'identification de l'utilisateur avec ce schéma d'authentification.<br /><br /> L’authentification Digest requiert l’utilisation de comptes de domaine Windows. Le domaine *Digest est* le nom de domaine Windows. Par conséquent, vous ne pouvez pas utiliser avec l’authentification Digest un serveur s’exécutant sur un système d’exploitation qui ne prend pas en charge les domaines Windows, tel que Windows XP Édition familiale. Inversement, lorsque le client s'exécute sur un système d'exploitation qui ne prend pas en charge les domaines Windows, un compte de domaine doit être spécifié explicitement lors de l'authentification.|  
|NTLM|L’authentification NTLM (NT LAN Manager) correspond à un schéma stimulation/réponse qui est une variation plus sécurisée de l’authentification Digest. Pour transformer les données de stimulation, NTLM utilise les informations d'identification Windows à la place du nom d'utilisateur et du mot de passe non chiffrés. L'authentification NTLM requiert plusieurs échanges entre le client et le serveur. Le serveur et tous les proxys qui interviennent doivent prendre en charge les connexions permanentes pour réussir l'authentification.|  
|Negotiate|L'authentification par négociation choisit automatiquement entre le protocole Kerberos et authentification NTLM, selon la disponibilité. Le protocole Kerberos est utilisé s'il est disponible ; dans le cas contraire, l'authentification NTLM est tentée. L'authentification Kerberos offre des améliorations importantes par rapport à NTLM. L'authentification Kerberos est plus rapide que l'authentification NTLM et elle permet l'utilisation de l'authentification mutuelle et de la délégation des informations d'identification aux ordinateurs distants.|  
|Windows Live ID|Le service HTTP Windows sous-jacent inclut une authentification qui utilise des protocoles fédérés. Toutefois, les transports HTTP standard dans WCF ne prennent pas en charge l’utilisation de schémas d’authentification fédérée, tels que Microsoft Windows Live ID. La prise en charge de cette fonctionnalité est actuellement disponible par le biais de l’utilisation de la sécurité de message. Pour plus d’informations, consultez [Fédération et jetons émis](federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Choix d'un schéma d'authentification  

 Lors de la sélection des schémas d'authentification possibles pour un serveur HTTP, voici quelques éléments à prendre en compte :  
  
- Considérez si la ressource doit être protégée. L'utilisation de l'authentification HTTP requiert la transmission de plus de données et peut limiter l'interopérabilité avec les clients. Autorisez un accès anonyme aux ressources qu'il n'est pas nécessaire de protéger.  
  
- Si la ressource doit être protégée, déterminez quels schémas d'authentification assurent le niveau de sécurité requis. Le schéma d'authentification standard le plus faible présenté ici correspond à l'authentification de base. L'authentification de base ne protège pas les informations d'identification de l'utilisateur. Le schéma d'authentification standard le plus fort est l'authentification par négociation, qui utilise le protocole Kerberos.  
  
- Un serveur ne doit présenter (dans les en-têtes WWW-Authenticate) aucun schéma qu'il n'est pas préparé à accepter ou qui ne sécurise pas de manière appropriée la ressource protégée. Les clients sont libres de choisir tout schéma d'authentification que le serveur présente. Certains clients utilisent par défaut un schéma d'authentification faible ou le premier schéma d'authentification qui figure dans la liste du serveur.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la sécurité des transports](transport-security-overview.md)
- [Utilisation de l'emprunt d'identité avec la sécurité de transport](using-impersonation-with-transport-security.md)
- [Délégation et emprunt d’identité](delegation-and-impersonation-with-wcf.md)
