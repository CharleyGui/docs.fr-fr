---
title: Comment lire à partir d’un fichier texte - Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705013"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Comment lire à partir d’un fichier texte (Guide de programmation C)
Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=nameWithType>.  
  
Pour un exemple <xref:System.IO.StreamReader>qui utilise , voir [Comment lire un fichier texte une ligne à la fois](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Les fichiers qui sont utilisés dans cet exemple sont créés dans le sujet [Comment écrire à un fichier texte](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a> Exemple  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez le code et collez-le dans une application console C#.  
  
Si vous n’utilisez pas les fichiers texte de Comment écrire `ReadAllText` `ReadAllLines` à un [fichier texte](./how-to-write-to-a-text-file.md), remplacez l’argument à et avec le chemin approprié et le nom de fichier sur votre ordinateur.
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié. Vérifiez le chemin et l’orthographe du nom de fichier.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Ne comptez pas sur le nom d’un fichier pour en déduire le contenu. Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](./index.md)
