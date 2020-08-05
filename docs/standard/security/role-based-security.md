---
title: Sécurité basée sur les rôles
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: ed6c33be5a5da066e238c160da8bff8d25cb68fc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555672"
---
# <a name="role-based-security"></a>Sécurité basée sur les rôles

Les rôles sont souvent utilisés dans les applications financières ou d'entreprise pour appliquer la stratégie. Ainsi, une application peut restreindre la taille de la transaction en cours, selon que l'utilisateur qui effectue la demande est membre d'un rôle spécifié. Par exemple, un employé est autorisé à exécuter les transactions se situant en deçà d’un seuil spécifié, tandis que le seuil applicable à un superviseur est plus élevé, et celui d’un vice-président plus élevé encore (ou inexistant). La sécurité basée sur les rôles peut également être utilisée quand l'application nécessite plusieurs approbations pour effectuer une action. C'est par exemple le cas d'un système d'achat dans lequel n'importe quel employé peut générer une demande d'achat, mais où seul un responsable des achats est habilité à convertir cette demande en bon de commande pour le transmettre à un fournisseur.  
  
 La sécurité basée sur les rôles .NET prend en charge l’autorisation en faisant en sorte que les informations relatives au principal, qui sont construites à partir d’une identité associée, soient disponibles pour le thread actuel. L'identité (et le principal qu'elle permet de définir) peut être basée sur un compte Windows ou être une identité personnalisée indépendante de tout compte Windows. Les applications .NET peuvent prendre des décisions d’autorisation en fonction de l’identité ou de l’appartenance au rôle du principal, ou les deux. Un rôle est un ensemble nommé de principaux qui disposent des mêmes privilèges en matière de sécurité (par exemple un caissier ou un responsable). Un principal peut être membre de plusieurs rôles. Ainsi, les applications peuvent utiliser l'appartenance d'un principal à un rôle pour déterminer si ce principal est autorisé à exécuter l'action demandée.  
  
 Pour faciliter l’utilisation et la cohérence avec la sécurité d’accès du code, la sécurité basée sur les rôles .NET fournit des <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objets qui permettent à l’Common Language Runtime d’effectuer l’autorisation d’une manière similaire aux contrôles de sécurité d’accès du code. La classe <xref:System.Security.Permissions.PrincipalPermission> représente l'identité ou le rôle que le principal doit avoir, et est à la fois compatible avec des contrôles de sécurité déclaratifs et impératifs. Vous pouvez également accéder directement aux informations se rapportant à l'identité du principal et effectuer des vérifications de rôle et d'identité dans votre code, si nécessaire.  
  
 .NET offre une prise en charge de la sécurité basée sur les rôles qui est suffisamment flexible et extensible pour répondre aux besoins d’un large éventail d’applications. Vous pouvez choisir d'interagir avec des infrastructures d'authentification existantes, telles que les services COM+ 1.0, ou de créer un système d'authentification personnalisé. La sécurité basée sur les rôles convient particulièrement aux applications web ASP.NET qui sont principalement traitées sur le serveur. Toutefois, la sécurité basée sur les rôles .NET peut être utilisée sur le client ou le serveur.  
  
 Avant de lire cette section, assurez-vous que vous comprenez les éléments présentés dans [concepts de sécurité clés](key-security-concepts.md).  
  
## <a name="see-also"></a>Voir aussi
  
- [Objets Principal et Identity](principal-and-identity-objects.md)
- [Concepts fondamentaux sur la sécurité](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [Sécurité ASP.NET Core](/aspnet/core/security/)
