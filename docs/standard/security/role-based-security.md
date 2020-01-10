---
title: Sécurité basée sur les rôles
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: 1dfb1f6246e86d6f565c9338fb09f34a1608e9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705923"
---
# <a name="role-based-security"></a>Sécurité basée sur les rôles
Les rôles sont souvent utilisés dans les applications financières ou d'entreprise pour appliquer la stratégie. Ainsi, une application peut restreindre la taille de la transaction en cours, selon que l'utilisateur qui effectue la demande est membre d'un rôle spécifié. Par exemple, un employé est autorisé à exécuter les transactions se situant en deçà d’un seuil spécifié, tandis que le seuil applicable à un superviseur est plus élevé, et celui d’un vice-président plus élevé encore (ou inexistant). La sécurité basée sur les rôles peut également être utilisée quand l'application nécessite plusieurs approbations pour effectuer une action. C'est par exemple le cas d'un système d'achat dans lequel n'importe quel employé peut générer une demande d'achat, mais où seul un responsable des achats est habilité à convertir cette demande en bon de commande pour le transmettre à un fournisseur.  
  
 La sécurité basée sur les rôles de .NET Framework prend en charge les autorisations en transmettant au thread actuel des informations sur les principaux, construits à partir d'une identité connexe. L'identité (et le principal qu'elle permet de définir) peut être basée sur un compte Windows ou être une identité personnalisée indépendante de tout compte Windows. Les applications .NET Framework peuvent accorder des autorisations en fonction de l'identité du principal, de son appartenance à un rôle, ou de ces deux éléments à la fois. Un rôle est un ensemble nommé de principaux qui disposent des mêmes privilèges en matière de sécurité (par exemple un caissier ou un responsable). Un principal peut être membre de plusieurs rôles. Ainsi, les applications peuvent utiliser l'appartenance d'un principal à un rôle pour déterminer si ce principal est autorisé à exécuter l'action demandée.  
  
 Pour une plus grande convivialité et pour améliorer la cohérence avec la sécurité d'accès du code, la sécurité basée sur les rôles de .NET Framework utilise des objets <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> qui permettent au Common Language Runtime d'octroyer des autorisations similaires à celles accordées dans le cadre de contrôles de sécurité d'accès du code. La classe <xref:System.Security.Permissions.PrincipalPermission> représente l'identité ou le rôle que le principal doit avoir, et est à la fois compatible avec des contrôles de sécurité déclaratifs et impératifs. Vous pouvez également accéder directement aux informations se rapportant à l'identité du principal et effectuer des vérifications de rôle et d'identité dans votre code, si nécessaire.  
  
 Le .NET Framework offre une prise en charge de la sécurité basée sur les rôles suffisamment flexible et extensible pour répondre aux exigences d'une vaste gamme d'applications. Vous pouvez choisir d'interagir avec des infrastructures d'authentification existantes, telles que les services COM+ 1.0, ou de créer un système d'authentification personnalisé. La sécurité basée sur les rôles convient particulièrement aux applications web ASP.NET qui sont principalement traitées sur le serveur. Toutefois, la sécurité basée sur les rôles de .NET Framework s'utilise aussi bien sur le client que sur le serveur.  
  
 Avant de lire cette section, assurez-vous que vous comprenez les éléments présentés dans [concepts de sécurité clés](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)|Explique comment configurer et gérer des principaux et des identités génériques et Windows.|  
|[Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)|Présente les concepts fondamentaux que vous devez comprendre avant d'utiliser la sécurité du .NET Framework.|  
  
## <a name="reference"></a>Reference  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
