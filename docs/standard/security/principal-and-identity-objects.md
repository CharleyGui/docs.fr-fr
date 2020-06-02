---
title: Objets Principal et Identity
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: cece51370fb269121e776e865275cd464c1af095
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291225"
---
# <a name="principal-and-identity-objects"></a>Objets Principal et Identity
Le code managé peut découvrir l’identité ou le rôle d’un principal à l’aide d’un <xref:System.Security.Principal.IPrincipal> objet, qui contient une référence à un <xref:System.Security.Principal.IIdentity> objet. Il peut être utile de comparer des objets identity et principal à des concepts familiers comme les comptes des utilisateurs et des groupes. Dans la plupart des environnements de réseau, les comptes d’utilisateur représentent des personnes ou des programmes, tandis que les comptes de groupe représentent des catégories d’utilisateurs et les droits qu’ils possèdent. De même, les objets identity .NET Framework représentent des utilisateurs, tandis que les rôles représentent des appartenances et des contextes de sécurité. Dans le .NET Framework, l’objet principal encapsule un objet identity et un rôle. Les applications .NET Framework accordent des droits au principal en fonction de son identité ou, plus fréquemment, de son appartenance au rôle.  
  
## <a name="identity-objects"></a>Objets Identity  
 L’objet identity encapsule des informations sur l’utilisateur ou l’une entité en cours de validation. Au niveau de base, les objets identity contiennent un nom et un type d’authentification. Le nom peut être un nom d’utilisateur ou le nom d’un compte Windows, tandis que le type d’authentification peut être un protocole de connexion pris en charge, tel que Kerberos V5, ou une valeur personnalisée. Le .NET Framework définit un <xref:System.Security.Principal.GenericIdentity> objet qui peut être utilisé pour la plupart des scénarios de connexion personnalisés et un objet plus spécialisé <xref:System.Security.Principal.WindowsIdentity> qui peut être utilisé lorsque vous souhaitez que votre application s’appuie sur l’authentification Windows. En outre, vous pouvez définir votre propre classe d’identité qui encapsule des informations utilisateur personnalisées.  
  
 L' <xref:System.Security.Principal.IIdentity> interface définit des propriétés pour accéder à un nom et à un type d’authentification, comme Kerberos V5 ou NTLM. Toutes les classes **Identity** implémentent l’interface **IIdentity**. Aucune relation n’est requise entre un objet **Identity** et le jeton de processus Windows NT sous lequel un thread est en cours d’exécution. Toutefois, si l’objet **Identity** est un objet **WindowsIdentity**, l’identité est supposée représenter un jeton de sécurité Windows NT.  
  
## <a name="principal-objects"></a>Objets Principal  
 L’objet principal représente le contexte de sécurité dans lequel le code est exécuté. Les applications qui implémentent une sécurité basée sur les rôles accordent des droits en fonction du rôle associé à un objet principal. À l’instar des objets Identity, le .NET Framework fournit un <xref:System.Security.Principal.GenericPrincipal> objet et un <xref:System.Security.Principal.WindowsPrincipal> objet. Vous pouvez également définir vos propres classes principal personnalisées.  
  
 L' <xref:System.Security.Principal.IPrincipal> interface définit une propriété pour accéder à un objet **Identity** associé, ainsi qu’une méthode pour déterminer si l’utilisateur identifié par l’objet **principal** est membre d’un rôle donné. Toutes les classes **Principal** implémentent l’interface **IPrincipal** ainsi que les propriétés et méthodes supplémentaires nécessaires. Par exemple, le common language runtime fournit la classe **WindowsPrincipal** qui implémente des fonctionnalités supplémentaires pour mapper l’appartenance au groupe Windows NT ou Windows 2000 avec des rôles.  
  
 Un objet **principal** est lié à un objet de contexte d’appel ( <xref:System.Runtime.Remoting.Messaging.CallContext> ) au sein d’un domaine d’application ( <xref:System.AppDomain> ). Un contexte d’appel par défaut est toujours créé avec chaque nouveau **AppDomain**. Un contexte d’appel est donc toujours disponible pour accepter l’objet **Principal**. Lorsqu’un nouveau thread est créé, un objet **CallContext** est également créé pour le thread. La référence de l’objet **Principal** est automatiquement copiée du thread de création dans l’objet **CallContext** du nouveau thread. Si le runtime ne peut pas déterminer quel objet **Principal** appartient au créateur du thread, il suit la stratégie par défaut de création d’un objet **Principal** et **Identity**.  
  
 Une stratégie spécifique de domaine d’application configurable définit les règles permettant de déterminer le type d’objet **Principal** à associer à un nouveau domaine d’application. Si la stratégie de sécurité le permet, le runtime peut créer des objets **Principal** et **Identity** qui correspondent au jeton de système d’exploitation associé au thread en cours d’exécution. Par défaut, le runtime utilise des objets **Principal** et **Identity** qui représentent des utilisateurs non authentifiés. Le runtime ne crée pas ces objets **Principal** et **Identity** par défaut tant que le code ne tente pas d’y accéder.  
  
 Le code approuvé créant un domaine d’application peut définir la stratégie de domaine d’application qui régit la construction des objets **Principal** et **Identity** par défaut. Cette stratégie spécifique du domaine d’application s’applique à tous les threads d’exécution dans ce domaine d’application. Un hôte approuvé non géré, par nature, a la possibilité de définir cette stratégie, mais le code managé qui définit cette stratégie doit avoir le <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pour le contrôle de la stratégie de domaine.  
  
 Lors de la transmission d’un objet **Principal** entre des domaines d’application, mais dans le même processus (et donc sur le même ordinateur), l’infrastructure distante copie une référence à l’objet **Principal** associé au contexte de l’appelant dans le contexte de l’appelé.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : créer un objet WindowsPrincipal](how-to-create-a-windowsprincipal-object.md)
- [Comment : créer des objets GenericPrincipal et GenericIdentity](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Remplacement d'un objet Principal](replacing-a-principal-object.md)
- [Emprunt et restauration d'identité](impersonating-and-reverting.md)
- [Sécurité basée sur les rôles](role-based-security.md)
- [Concepts fondamentaux sur la sécurité](key-security-concepts.md)
