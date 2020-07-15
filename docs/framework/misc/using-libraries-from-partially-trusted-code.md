---
title: Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
description: Savoir comment utiliser les bibliothèques à partir de code d’un degré de confiance partiel. Utilisez l’attribut AllowPartiallyTrustedCallersAttribute pour appeler des bibliothèques managées partagées.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
ms.openlocfilehash: d2e015e381a3778bbab9977af20897ce9f1955c1
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309220"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Cette rubrique traite du comportement des assemblys avec nom fort et s’applique uniquement aux assemblys de [niveau 1](security-transparent-code-level-1.md) . Le [code transparent de sécurité,](security-transparent-code-level-2.md) les assemblys de niveau 2 dans le .NET Framework 4 ou version ultérieure ne sont pas affectés par les noms forts. Pour plus d’informations sur les modifications apportées au système de sécurité, consultez [modifications de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Les applications qui n’ont pas reçu un niveau de confiance totale de la part de leur hôte ou bac à sable (sandbox) ne sont pas autorisées à appeler les bibliothèques managées partagées, sauf si le créateur de la bibliothèque les autorise explicitement à passer outre l’utilisation de l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Par conséquent, les auteurs d'applications doivent être conscients que certaines bibliothèques pas seront disponibles dans un contexte de confiance partielle. Par défaut, tout le code qui s’exécute dans un bac à [sable (sandbox)](how-to-run-partially-trusted-code-in-a-sandbox.md) de confiance partielle et ne figure pas dans la liste des assemblys de confiance totale est partiellement approuvé. S'il n'est pas prévu que votre code soit exécuté dans un contexte de confiance partielle ou qu'il soit appelé par du code partiellement fiable, les informations de cette section ne vous concernent pas. Toutefois, si vous écrivez du code qui doit interagir avec du code partiellement fiable ou fonctionner dans un contexte de confiance partiel, vous devez prendre en compte les éléments suivants :  
  
- Les bibliothèques doivent être signées avec un nom fort pour pouvoir être partagées par plusieurs applications. Les noms forts permettent à votre code d'être placé dans un Global Assembly Cache ou d'être ajouté à la liste de confiance totale d'un bac à sable <xref:System.AppDomain>. De plus, ils permettent aux utilisateurs de vérifier qu'une portion du code mobile provient bien de vous.  
  
- Par défaut, les bibliothèques partagées de [niveau 1](security-transparent-code-level-1.md) avec nom fort effectuent automatiquement un [LinkDemand](link-demands.md) implicite pour une confiance totale, sans que le writer de bibliothèque ait à faire quoi que ce soit.  
  
- Si un appelant ne dispose pas d'une confiance totale et tente d'appeler ce type de bibliothèque, le runtime lève une <xref:System.Security.SecurityException> et l'appelant n'est pas autorisé à se connecter à la bibliothèque.  
  
- Pour désactiver le **LinkDemand** automatique et empêcher la levée de l’exception, vous pouvez placer l’attribut **AllowPartiallyTrustedCallersAttribute** sur l’étendue de l’assembly d’une bibliothèque partagée. Cet attribut permet à vos bibliothèques d'être appelées depuis du code managé partiellement fiable.  
  
- Le code partiellement fiable qui reçoit l'accès à une bibliothèque possédant cet attribut est toujours soumis à des restrictions supplémentaires définies par <xref:System.AppDomain>.  
  
- Il n’existe pas de méthode par programmation pour le code partiellement fiable pour appeler une bibliothèque qui n’a pas l’attribut **AllowPartiallyTrustedCallersAttribute** .  
  
 Les bibliothèques qui sont privées pour une application spécifique ne nécessitent pas de nom fort ou d’attribut **AllowPartiallyTrustedCallersAttribute** et ne peuvent pas être référencées par du code potentiellement malveillant en dehors de l’application. Ce code est protégé contre toute mauvaise utilisation, intentionnelle ou non, par du code mobile partiellement fiable, sans que le développeur n'ait à intervenir.  
  
 Vous devez envisager d'activer explicitement l'utilisation des types de code suivants pour le code partiellement fiable :  
  
- Code qui a été soigneusement testé pour identifier les vulnérabilités de sécurité et qui est conforme aux instructions décrites dans [instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md).  
  
- Les bibliothèques de code avec nom fort qui sont écrites spécifiquement pour les scénarios de confiance partielle.  
  
- Tous les composants (partiellement ou entièrement fiables) signés avec un nom fort qui seront appelés par du code téléchargé depuis Internet.  
  
> [!NOTE]
> Certaines classes de la bibliothèque de classes .NET Framework n’ont pas l’attribut **AllowPartiallyTrustedCallersAttribute** et ne peuvent pas être appelées par du code de confiance partielle.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès du code](code-access-security.md)
