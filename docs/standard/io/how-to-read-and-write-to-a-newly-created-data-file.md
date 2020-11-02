---
title: 'Comment : lire et écrire dans un fichier de données nouvellement créé'
description: Découvrez comment lire et écrire dans un fichier de données nouvellement créé dans .NET à l’aide des classes System. IO. BinaryReader et System. IO. BinaryWriter.
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET], reading data
- I/O [.NET], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 236d50260efa66f21db6d0abba6cc5c258a74d8d
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188729"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Comment : lire et écrire dans un fichier de données nouvellement créé

Les classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> et <xref:System.IO.BinaryReader?displayProperty=nameWithType> sont utilisées pour écrire et lire des données autres que des chaînes de caractères. L’exemple suivant montre comment créer un flux de fichier vide, y écrire des données, puis les lire.

L’exemple créé un fichier de données appelé *Test.data* dans le répertoire actif, crée les objets <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> associés, puis utilise l’objet <xref:System.IO.BinaryWriter> pour écrire les entiers de 0 à 10 dans *Test.data* , ce qui laisse le pointeur de fichier à la fin du fichier. Ensuite, l’objet <xref:System.IO.BinaryReader> replace le pointeur de fichier au début, puis lit le contenu spécifié.  
  
> [!NOTE]
> Si *Test.data* existe déjà dans le répertoire actif, une exception <xref:System.IO.IOException> est levée. Utilisez l’option de mode de fichier <xref:System.IO.FileMode.Create?displayProperty=nameWithType> plutôt que <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> pour toujours créer un fichier sans lever d’exception.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Comment : énumérer des répertoires et des fichiers](how-to-enumerate-directories-and-files.md)  
- [Procédure : ouvrir un fichier journal et y ajouter des éléments](how-to-open-and-append-to-a-log-file.md)  
- [Comment : lire du texte à partir d’un fichier](how-to-read-text-from-a-file.md)  
- [Comment : écrire du texte dans un fichier](how-to-write-text-to-a-file.md)  
- [Comment : lire les caractères d’une chaîne](how-to-read-characters-from-a-string.md)  
- [Comment : écrire des caractères dans une chaîne](how-to-write-characters-to-a-string.md)  
- [E/s de fichier et de flux](index.md)
