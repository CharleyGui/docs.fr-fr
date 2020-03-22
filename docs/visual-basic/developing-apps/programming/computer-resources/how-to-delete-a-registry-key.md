---
title: 'Comment : supprimer une clé de Registre'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345654"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Guide pratique pour supprimer une clé de Registre en Visual Basic

Vous pouvez utiliser les méthodes<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> et <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> pour supprimer les clés de Registre.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-delete-a-registry-key"></a>Pour supprimer une clé de Registre  
  
- Utilisez la méthode `DeleteSubKey` pour supprimer une clé de Registre. Cet exemple supprime la clé Software/TestApp dans la ruche CurrentUser. Vous pouvez spécifier la chaîne appropriée dans le code ou faire en sorte que celui-ci repose sur des informations fournies par l’utilisateur.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 La méthode `DeleteSubKey` retourne une chaîne vide si la paire clé/valeur n’existe pas.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).  
  
- L’utilisateur ne dispose pas des autorisations pour supprimer des clés de Registre (<xref:System.Security.SecurityException>).  
  
- Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).  
  
- La clé de Registre est en lecture seule (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Les appels au Registre échouent quand l’utilisateur ne dispose pas des autorisations d’exécution nécessaires (<xref:System.Security.Permissions.RegistryPermission>) ou de l’accès correct (tel que déterminé par les listes de contrôle d’accès) pour créer ou écrire des paramètres. Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Sécurité et Registre](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Lecture et écriture dans le Registre](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
