---
title: Guide de programmation C# pour lire un fichier texte une ligne à la fois
description: Découvrez comment lire un fichier texte ligne par ligne. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 1e29013b1008e1000c23804dc3056014cc7c104b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301955"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a>Guide pratique pour lire un fichier texte ligne par ligne (Guide de programmation C#)
Cet exemple lit le contenu d’une chaîne d’un fichier texte, ligne par ligne, à l’aide de la méthode `ReadLine` de la classe `StreamReader`. Chaque ligne de texte est stockée dans la chaîne `line` et s’affiche à l’écran.  
  
## <a name="example"></a>Exemple  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez le code et collez-le dans la méthode `Main` d’une application console.  
  
 Remplacez `"c:\test.txt"` par le nom du fichier.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier n’existe pas.  
  
## <a name="net-security"></a>Sécurité .NET  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](./index.md)
