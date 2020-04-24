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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645718"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Ce sujet aborde le comportement des assemblées de nom fort et ne s’applique qu’aux assemblages de [niveau 1.](security-transparent-code-level-1.md) Code transparent sur la sécurité, les assemblages [de niveau 2](security-transparent-code-level-2.md) du cadre .NET 4 ou plus tard ne sont pas affectés par des noms forts. Pour plus d’informations sur les changements apportés au système de sécurité, voir [Changements de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Les applications qui n’ont pas reçu un niveau de confiance totale de la part de leur hôte ou bac à sable (sandbox) ne sont pas autorisées à appeler les bibliothèques managées partagées, sauf si le créateur de la bibliothèque les autorise explicitement à passer outre l’utilisation de l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Par conséquent, les auteurs d'applications doivent être conscients que certaines bibliothèques pas seront disponibles dans un contexte de confiance partielle. Par défaut, tout le code qui s’exécute dans un bac à [sable](how-to-run-partially-trusted-code-in-a-sandbox.md) de confiance partielle et qui ne figure pas dans la liste des assemblages en pleine confiance est partiellement fiable. S'il n'est pas prévu que votre code soit exécuté dans un contexte de confiance partielle ou qu'il soit appelé par du code partiellement fiable, les informations de cette section ne vous concernent pas. Toutefois, si vous écrivez du code qui doit interagir avec du code partiellement fiable ou fonctionner dans un contexte de confiance partiel, vous devez prendre en compte les éléments suivants :  
  
- Les bibliothèques doivent être signées avec un nom fort pour pouvoir être partagées par plusieurs applications. Les noms forts permettent à votre code d'être placé dans un Global Assembly Cache ou d'être ajouté à la liste de confiance totale d'un bac à sable <xref:System.AppDomain>. De plus, ils permettent aux utilisateurs de vérifier qu'une portion du code mobile provient bien de vous.  
  
- Par défaut, les bibliothèques partagées [de niveau 1,](security-transparent-code-level-1.md) nommées par un fort niveau 1, exécutent automatiquement un [LinkDemand](link-demands.md) implicite pour la pleine confiance, sans que l’auteur de la bibliothèque n’ait à faire quoi que ce soit.  
  
- Si un appelant ne dispose pas d'une confiance totale et tente d'appeler ce type de bibliothèque, le runtime lève une <xref:System.Security.SecurityException> et l'appelant n'est pas autorisé à se connecter à la bibliothèque.  
  
- Afin de désactiver le **LinkDemand** automatique et d’empêcher l’exception d’être jeté, vous pouvez placer **l’attribut AllowPartiallyTrustedCallersAttribute** sur la portée d’assemblage d’une bibliothèque partagée. Cet attribut permet à vos bibliothèques d'être appelées depuis du code managé partiellement fiable.  
  
- Le code partiellement fiable qui reçoit l'accès à une bibliothèque possédant cet attribut est toujours soumis à des restrictions supplémentaires définies par <xref:System.AppDomain>.  
  
- Il n’existe aucun moyen programmatique pour le code partiellement fiable d’appeler une bibliothèque qui n’a pas **l’attribut AllowPartiallyTrustedCallersAttribute.**  
  
 Les bibliothèques qui sont privées d’une application spécifique ne nécessitent pas un nom fort ou **l’attribut AllowPartiallyTrustedCallersAttribute** et ne peuvent pas être référencées par un code potentiellement malveillant en dehors de l’application. Ce code est protégé contre toute mauvaise utilisation, intentionnelle ou non, par du code mobile partiellement fiable, sans que le développeur n'ait à intervenir.  
  
 Vous devez envisager d'activer explicitement l'utilisation des types de code suivants pour le code partiellement fiable :  
  
- Code qui a été testé avec diligence pour les vulnérabilités de sécurité et est conforme aux lignes directrices décrites dans [secure Coding Guidelines](../../standard/security/secure-coding-guidelines.md).  
  
- Les bibliothèques de code avec nom fort qui sont écrites spécifiquement pour les scénarios de confiance partielle.  
  
- Tous les composants (partiellement ou entièrement fiables) signés avec un nom fort qui seront appelés par du code téléchargé depuis Internet.  
  
> [!NOTE]
> Certaines classes de la bibliothèque de classe Cadre .NET n’ont pas **l’attribut AllowPartiallyTrustedCallersAttribute** et ne peuvent pas être appelées par un code partiellement fiable.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès au code](code-access-security.md)
