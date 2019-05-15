---
title: 'Procédure : Créer une clé dans le Registre (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 0982baea2327daf23726ef269d53388d6011703d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596146"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Procédure : Créer une clé dans le Registre (Visual C#)
Cet exemple ajoute la paire de valeurs « Name » et « Isabella » dans le Registre de l’utilisateur actuel, sous la clé « Names ».  
  
## <a name="example"></a>Exemple  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Copiez le code et collez-le dans la méthode `Main` d’une application console.  
  
- Remplacez le paramètre `Names` par le nom d’une clé qui existe directement sous le nœud HKEY_CURRENT_USER du Registre.  
  
- Remplacez le paramètre `Name` par le nom d’une valeur qui existe directement sous le nœud Names.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Examinez la structure du Registre pour rechercher un emplacement approprié pour votre clé. Par exemple, vous souhaiterez peut-être ouvrir la clé Software de l’utilisateur actuel et créer une clé avec le nom de votre société. Ensuite, ajoutez les valeurs de Registre à la clé de votre société.  
  
 Les conditions ci-dessous peuvent générer une exception :  
  
- Le nom de la clé est null.  
  
- L’utilisateur ne dispose pas des autorisations nécessaires pour créer des clés de Registre.  
  
- Le nom de la clé dépasse la limite de 255 caractères.  
  
- La clé est fermée.  
  
- La clé de Registre est en lecture seule.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il est plus sûr d’écrire des données dans le dossier utilisateur (`Microsoft.Win32.Registry.CurrentUser`) que sur l’ordinateur local (`Microsoft.Win32.Registry.LocalMachine`).  
  
 Quand vous créez une valeur de Registre, vous devez déterminer ce qu’il faut faire si cette valeur existe déjà. Il est possible qu’un autre processus, éventuellement malveillant, ait déjà créé la valeur et y ait accès. Quand vous placez des données dans la valeur de Registre, ces données sont accessibles à l’autre processus. Pour éviter ce problème, utilisez la méthode `Overload:Microsoft.Win32.RegistryKey.GetValue` . Elle retourne null si la clé n’existe pas encore.  
  
 Il est dangereux de stocker des données confidentielles, telles que des mots de passe, dans le Registre sous forme de texte brut, même si la clé de Registre est protégée par des listes de contrôle d’accès.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
- [Read, write and delete from the registry with C# (Lire, écrire et supprimer du Registre avec C#)](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
