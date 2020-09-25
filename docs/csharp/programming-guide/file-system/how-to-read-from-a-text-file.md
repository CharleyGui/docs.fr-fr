---
title: Comment lire un fichier texte-Guide de programmation C#
description: Apprenez à lire à partir d’un fichier texte à l’aide de méthodes statiques de la classe file. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 64ac99ec0a72ba7df120f6732edccf160a351738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201835"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Comment lire un fichier texte (Guide de programmation C#)

Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=nameWithType>.  
  
Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader> , consultez [Comment lire un fichier texte ligne par ligne](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Les fichiers utilisés dans cet exemple sont créés dans la rubrique [Comment écrire dans un fichier texte](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Exemple  

 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Copiez le code et collez-le dans une application console C#.  
  
Si vous n’utilisez pas les fichiers texte à partir de la [procédure d’écriture dans un fichier texte](./how-to-write-to-a-text-file.md), remplacez l’argument par `ReadAllText` et `ReadAllLines` par le chemin d’accès et le nom de fichier appropriés sur votre ordinateur.
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié. Vérifiez le chemin et l’orthographe du nom de fichier.  
  
## <a name="net-security"></a>Sécurité .NET  

 Ne comptez pas sur le nom d’un fichier pour en déduire le contenu. Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](./index.md)
