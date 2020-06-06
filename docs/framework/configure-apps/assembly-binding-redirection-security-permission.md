---
title: Autorisation de sécurité pour la redirection de liaison d’assembly
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921375"
---
# <a name="assembly-binding-redirection-security-permission"></a>Autorisation de sécurité pour la redirection de liaison d’assembly
La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité. Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers. L’autorisation est accordée en définissant l' <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur <xref:System.Security.Permissions.SecurityPermission> . Les assemblys managés n’ont pas d’autorisations par défaut.  
  
 L’autorisation de sécurité est accordée aux applications qui s’exécutent dans la zone de confiance (ordinateur local) et la zone intranet. Les applications qui s’exécutent dans la zone Internet ne sont pas strictement autorisées à effectuer une redirection de liaison d’assembly.  
  
 L’autorisation n’est pas requise si la redirection d’assembly est effectuée dans un fichier de stratégie d’éditeur contrôlé par l’éditeur du composant ou dans le fichier de configuration de l’ordinateur contrôlé par l’administrateur. Toutefois, l’autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) de l’élément dans le fichier de configuration de l’application.  
  
 Le tableau suivant présente les paramètres de sécurité par défaut de l’indicateur **BindingRedirects** .  
  
|Zone|Paramètre de l’indicateur BindingRedirects|  
|----------|-----------------------------------|  
|Zone approuvée (ordinateur local)|**ON**|  
|Zone Intranet|**ON**|  
|Zone Internet|**OFF**|  
|Zones non approuvées|**OFF**|  
  
 Un administrateur peut modifier ces paramètres de sécurité pour prendre en charge ou restreindre des scénarios spécifiques sur un ordinateur donné. Il n’existe aucun outil permettant de modifier le paramètre d’indicateur **BindingRedirects** à partir de la valeur par défaut ; un administrateur doit modifier manuellement le fichier Security. config sur l’ordinateur de l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi

- [Exécution côte à côte et fichiers de stratégie de l'éditeur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Procédure : Activer et désactiver la redirection de liaison automatique](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Exécution côte à côte](../deployment/side-by-side-execution.md)
