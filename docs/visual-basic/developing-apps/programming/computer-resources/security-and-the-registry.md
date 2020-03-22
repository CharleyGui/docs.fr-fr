---
title: Sécurité et Registre
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345486"
---
# <a name="security-and-the-registry-visual-basic"></a>Sécurité et Registre (Visual Basic)

Cette page décrit les implications en matière de sécurité du stockage des données dans le Registre.  
  
## <a name="permissions"></a>Autorisations  

 Il est dangereux de stocker des données confidentielles (comme des mots de passe) dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.  
  
 L’utilisation du Registre peut compromettre la sécurité en accordant un accès inapproprié à des ressources système ou à des informations protégées. Pour utiliser ces propriétés, vous devez disposer des autorisations de lecture et d’écriture de l’énumération <xref:System.Security.Permissions.RegistryPermissionAccess>, qui contrôle l’accès aux variables de Registre. Tout code s’exécutant avec une confiance totale (sous la stratégie de sécurité par défaut, il s’agit de n’importe quel code installé sur le disque dur local de l’utilisateur) dispose des autorisations nécessaires pour accéder au Registre. Pour plus d'informations, consultez la classe <xref:System.Security.Permissions.RegistryPermission>.  
  
 Les variables de Registre ne doivent pas être stockées dans des emplacements de mémoire où du code sans <xref:System.Security.Permissions.RegistryPermission> peut y accéder. De même, quand vous accordez des autorisations, accordez les privilèges minimaux nécessaires pour effectuer la tâche.  
  
 Les valeurs des autorisations d’accès au Registre sont définies par l’énumération <xref:System.Security.Permissions.RegistryPermissionAccess>. Le tableau suivant détaille ses membres.  
  
|Valeur|Accès aux variables de Registre|  
|-----------|----------------------------------|  
|`AllAccess`|Créer, lire et écrire|  
|`Create`|Créer|  
|`NoAccess`|Aucun accès|  
|`Read`|Lire|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Vérification des valeurs dans les clés de Registre  

 Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà. Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès. Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus. Pour l’éviter, utilisez la méthode `GetValue`. Elle retourne `Nothing` si la clé n’existe pas encore.  
  
> [!IMPORTANT]
> Lors de la lecture du Registre à partir d’une application web, l’identité de l’utilisateur actuel dépend de l’authentification et de l’emprunt d’identité implémentés dans l’application web.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Lecture et écriture dans le Registre](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
