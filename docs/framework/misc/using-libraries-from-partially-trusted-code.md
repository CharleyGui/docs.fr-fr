---
title: Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d858ef4c2f70c55b0a36e845f90d9a8e08f5e2d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487827"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Cette rubrique aborde le comportement des assemblys avec nom fort et s’applique uniquement aux [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblys. [Code Transparent de sécurité, niveau 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblys dans le .NET Framework 4 ou version ultérieure ne sont pas affectées par les noms forts. Pour plus d’informations sur les modifications apportées au système de sécurité, consultez [modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
 Les applications qui n’ont pas reçu un niveau de confiance totale de la part de leur hôte ou bac à sable (sandbox) ne sont pas autorisées à appeler les bibliothèques managées partagées, sauf si le créateur de la bibliothèque les autorise explicitement à passer outre l’utilisation de l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Par conséquent, les auteurs d'applications doivent être conscients que certaines bibliothèques pas seront disponibles dans un contexte de confiance partielle. Par défaut, tout le code qui s’exécute dans un niveau de confiance partiel [bac à sable](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) et n’est pas dans la liste des assemblys de confiance totale est partiellement approuvée. S'il n'est pas prévu que votre code soit exécuté dans un contexte de confiance partielle ou qu'il soit appelé par du code partiellement fiable, les informations de cette section ne vous concernent pas. Toutefois, si vous écrivez du code qui doit interagir avec du code partiellement fiable ou fonctionner dans un contexte de confiance partiel, vous devez prendre en compte les éléments suivants :  
  
- Les bibliothèques doivent être signées avec un nom fort pour pouvoir être partagées par plusieurs applications. Les noms forts permettent à votre code d'être placé dans un Global Assembly Cache ou d'être ajouté à la liste de confiance totale d'un bac à sable <xref:System.AppDomain>. De plus, ils permettent aux utilisateurs de vérifier qu'une portion du code mobile provient bien de vous.  
  
- Par défaut, avec nom fort [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md) bibliothèques partagées effectuent implicite [LinkDemand](../../../docs/framework/misc/link-demands.md) de confiance totale automatiquement, sans rien à faire le writer de bibliothèque.  
  
- Si un appelant ne dispose pas d'une confiance totale et tente d'appeler ce type de bibliothèque, le runtime lève une <xref:System.Security.SecurityException> et l'appelant n'est pas autorisé à se connecter à la bibliothèque.  
  
- Afin de désactiver l’automatique **LinkDemand** et empêcher l’exception ne soit levée, vous pouvez placer le **AllowPartiallyTrustedCallersAttribute** attribut sur l’étendue de l’assembly d’un partage bibliothèque. Cet attribut permet à vos bibliothèques d'être appelées depuis du code managé partiellement fiable.  
  
- Le code partiellement fiable qui reçoit l'accès à une bibliothèque possédant cet attribut est toujours soumis à des restrictions supplémentaires définies par <xref:System.AppDomain>.  
  
- Il n’existe aucun moyen de programmation pour le code partiellement fiable d’appeler une bibliothèque qui n’a pas la **AllowPartiallyTrustedCallersAttribute** attribut.  
  
 Les bibliothèques qui sont privées pour une application particulière ne nécessitent pas un nom fort ou le **AllowPartiallyTrustedCallersAttribute** attribut et ne peuvent pas être référencées par du code potentiellement malveillant en dehors de l’application. Ce code est protégé contre toute mauvaise utilisation, intentionnelle ou non, par du code mobile partiellement fiable, sans que le développeur n'ait à intervenir.  
  
 Vous devez envisager d'activer explicitement l'utilisation des types de code suivants pour le code partiellement fiable :  
  
- Code qui a été soigneusement testé des vulnérabilités de sécurité et est conforme aux indications décrites dans [instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md).  
  
- Les bibliothèques de code avec nom fort qui sont écrites spécifiquement pour les scénarios de confiance partielle.  
  
- Tous les composants (partiellement ou entièrement fiables) signés avec un nom fort qui seront appelés par du code téléchargé depuis Internet.  
  
> [!NOTE]
>  Certaines classes dans la bibliothèque de classes .NET Framework n’ont pas la **AllowPartiallyTrustedCallersAttribute** attribut et ne peut pas être appelée par du code partiellement fiable.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès du code](../../../docs/framework/misc/code-access-security.md)
