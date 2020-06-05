---
title: 'Procédure : lire une valeur à partir d’une clé de Registre'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 74069b111f4316eb81c74f5e62c1fbff6ab8f4b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401847"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Guide pratique pour lire une valeur à partir d'une clé de Registre en Visual Basic

La méthode `GetValue` de l’objet `My.Computer.Registry` peut être utilisée pour lire les valeurs dans le Registre Windows.  
  
 Si la clé « Software\MyApp » de l’exemple suivant n’existe pas, une exception est levée. Si le `ValueName` (« Name » dans l’exemple suivant) n’existe pas, `Nothing` est retourné.  
  
 La méthode `GetValue` peut également être utilisée pour déterminer si une valeur donnée existe dans une clé de Registre spécifique.  
  
 Lorsque le code lit le contenu du Registre à partir d’une application web, l’utilisateur actuel est déterminé par l’authentification et par l’emprunt d’identité implémenté dans l’application web.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Pour lire une valeur dans une clé de Registre  
  
- Utilisez la méthode `GetValue`, en spécifiant un chemin et un nom, pour lire une valeur dans une clé de Registre. L’exemple suivant lit la valeur `Name` dans `HKEY_CURRENT_USER\Software\MyApp` et l’affiche dans la boîte de message.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Système d’exploitation Windows > Registre**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Pour déterminer si une clé existe dans une clé de Registre  
  
- Utilisez la méthode `GetValue` pour récupérer la valeur. Le code suivant vérifie si la valeur existe et retourne un message si elle n’existe pas.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Le Registre contient les clés de niveau supérieur, ou racine, qui sont utilisées pour stocker des données. Par exemple, la clé racine HKEY_LOCAL_MACHINE est utilisée pour stocker des paramètres d’ordinateur utilisés par tous les utilisateurs, tandis que HKEY_CURRENT_USER est utilisée pour stocker des données spécifiques à un utilisateur.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le nom de la clé est `Nothing` (<xref:System.ArgumentNullException>).  
  
- L’utilisateur ne dispose pas des autorisations nécessaires pour lire des clés de Registre (<xref:System.Security.SecurityException>).  
  
- Le nom de la clé dépasse la limite de 255 caractères (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Pour exécuter ce processus, votre assembly nécessite un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. De même, l’utilisateur doit disposer de listes de contrôle d’accès (ACL) valides pour créer ou écrire des paramètres. Par exemple, une application locale qui dispose de l’autorisation de sécurité d’accès du code peut ne pas disposer des autorisations de système d’exploitation. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Lecture et écriture dans le Registre](reading-from-and-writing-to-the-registry.md)
