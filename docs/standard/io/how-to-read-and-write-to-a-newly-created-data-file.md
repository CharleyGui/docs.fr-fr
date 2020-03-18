---
title: 'Comment : Lire et écrire dans un fichier de données nouvellement créé'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155748"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Comment : Lire et écrire dans un fichier de données nouvellement créé
Les classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> et <xref:System.IO.BinaryReader?displayProperty=nameWithType> sont utilisées pour écrire et lire des données autres que des chaînes de caractères. L’exemple suivant montre comment créer un flux de fichier vide, y écrire des données, puis les lire.

L’exemple créé un fichier de données appelé *Test.data* dans le répertoire actif, crée les objets <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> associés, puis utilise l’objet <xref:System.IO.BinaryWriter> pour écrire les entiers de 0 à 10 dans *Test.data*, ce qui laisse le pointeur de fichier à la fin du fichier. Ensuite, l’objet <xref:System.IO.BinaryReader> replace le pointeur de fichier au début, puis lit le contenu spécifié.  
  
> [!NOTE]
> Si *Test.data* existe déjà dans le répertoire actif, une exception <xref:System.IO.IOException> est levée. Utilisez l’option de mode de fichier <xref:System.IO.FileMode.Create?displayProperty=nameWithType> plutôt que <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> pour toujours créer un fichier sans lever d’exception.  
  
## <a name="example"></a> Exemple  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Comment : Énumérer les répertoires et les fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Comment : Ouvrez et appendicez à un fichier journal](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Comment: Lire le texte d’un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Comment: Écrire du texte à un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Comment: Lire les personnages d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Comment: Écrire des personnages à une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de fichier et de flux](../../../docs/standard/io/index.md)
