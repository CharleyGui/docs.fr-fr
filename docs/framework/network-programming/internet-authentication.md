---
title: Authentification Internet
description: Découvrez les différents mécanismes d’authentification client que les classes System.Net prennent en charge pour vos applications dans le .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 085ca27dd0cfedc90211b21c10cc8bc5cf1ecd21
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241588"
---
# <a name="internet-authentication"></a>Authentification Internet

Les classes <xref:System.Net> prennent en charge divers mécanismes d’authentification client, parmi lesquels les méthodes d’authentification Internet standard (de base, Digest, Negotiate, NTLM et Kerberos) et les méthodes personnalisées que vous pouvez créer.  
  
 Les informations d’identification utilisées pour l’authentification sont stockées dans les classes <xref:System.Net.NetworkCredential> et <xref:System.Net.CredentialCache>, qui implémentent l’interface <xref:System.Net.ICredentials>. Quand une de ces classes est interrogée pour fournir des informations d’identification, elle retourne une instance de la classe **NetworkCredential**. Le processus d’authentification est géré par la classe <xref:System.Net.AuthenticationManager>, mais il est en réalité effectué par une classe du module d’authentification qui implémente l’interface <xref:System.Net.IAuthenticationModule>. Pour pouvoir utiliser un module d’authentification personnalisé, vous devez préalablement l’inscrire avec **AuthenticationManager**. Les modules pour les méthodes d’authentification de base, Digest, Negotiate, NTLM et Kerberos sont inscrits par défaut.  
  
 La classe **NetworkCredential** stocke un ensemble d’informations d’identification qui sont associées à une ressource Internet identifiée de manière unique par un URI et retourne ces informations en réponse à chaque appel de la méthode <xref:System.Net.NetworkCredential.GetCredential%2A>. La classe **NetworkCredential** est généralement utilisée dans les applications qui accèdent à un nombre limité de ressources Internet ou dans celles qui utilisent toujours le même ensemble d’informations d’identification.  
  
 La classe **CredentialCache** stocke un ensemble d’informations d’identification pour diverses ressources web. Quand la méthode <xref:System.Net.CredentialCache.GetCredential%2A> est appelée, **CredentialCache** retourne l’ensemble approprié d’informations d’identification, qui est déterminé par l’URI de la ressource web et le schéma d’authentification demandé. La classe **CredentialCache** est appropriée pour les applications qui utilisent diverses ressources Internet avec des schémas d’authentification différents, car elle peut stocker toutes les informations d’identification et les fournir en réponse à une demande.  
  
 Quand une ressource Internet fait une demande d’authentification, la méthode <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> envoie <xref:System.Net.WebRequest> à **AuthenticationManager** en même temps que la demande des informations d’identification. La demande est ensuite authentifiée selon le processus suivant :  
  
1. **AuthenticationManager** appelle la méthode <xref:System.Net.IAuthenticationModule.Authenticate%2A> sur chacun des modules d’authentification inscrits, dans l’ordre de leur inscription. **AuthenticationManager** utilise le premier module qui ne retourne pas la valeur **Null** pour effectuer le processus d’authentification. Ce processus peut varier en fonction du type de module d’authentification utilisé.  
  
2. À la fin du processus d’authentification, le module d’authentification retourne <xref:System.Net.Authorization> à la classe **WebRequest** qui contient les informations nécessaires pour accéder à la ressource Internet.  
  
 Certains schémas d’authentification authentifient un utilisateur sans faire de demande de ressource au préalable. Une application peut gagner du temps en effectuant une pré-authentification de la ressource, ce qui évite au moins un aller-retour avec le serveur. Elle peut aussi effectuer l’authentification au démarrage du programme pour être plus réactive avec l’utilisateur ultérieurement. Les schémas d’authentification qui peuvent utiliser la pré-authentification ont leur propriété <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> définie sur **true**.  
  
## <a name="see-also"></a>Voir aussi

- [Authentification de base et authentification Digest](basic-and-digest-authentication.md)
- [Authentification NTLM et Kerberos](ntlm-and-kerberos-authentication.md)
- [Sécurité dans la programmation réseau](security-in-network-programming.md)
