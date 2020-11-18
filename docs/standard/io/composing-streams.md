---
title: Composer des flux
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
ms.openlocfilehash: c50a372ee3434fcd7f72ad707ca82c5c9ad8a5c8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823379"
---
# <a name="compose-streams"></a>Composer des flux
Un *magasin* de stockage est un support de stockage, tel qu’un disque ou une mémoire. Chaque magasin de stockage implémente son propre flux en tant qu’implémentation de la classe <xref:System.IO.Stream>.

Chaque type de flux lit et écrit des octets depuis et vers le magasin de stockage donné. Les flux qui se connectent aux magasins de stockage sont appelés des *flux de base*. Les flux de base comprennent des constructeurs qui ont les paramètres nécessaires pour connecter le flux au magasin de stockage. Par exemple, <xref:System.IO.FileStream> comprend des constructeurs qui spécifient un paramètre de chemin, qui indique la façon dont le fichier est partagé par les processus.  

La conception des classes <xref:System.IO> fournit une composition simplifiée des flux. Vous pouvez attacher des flux de base à un ou plusieurs flux directs qui fournissent les fonctionnalités souhaitées. Vous pouvez attacher un lecteur ou un enregistreur à la fin de la chaîne pour que les types préférés puissent être lus ou écrits facilement.  

L’exemple de code suivant crée un **FileStream** autour du fichier *MyFile.txt* existant afin de placer *MyFile.txt* dans la mémoire tampon. Notez que les **FileStreams** sont mis en mémoire tampon par défaut.

>[!IMPORTANT]
>L’exemple suppose qu’un fichier nommé *MyFile.txt* existe déjà dans le dossier où se trouve l’application.  

## <a name="example-use-streamreader"></a>Exemple : utilisation de StreamReader
L’exemple suivant crée un <xref:System.IO.StreamReader> pour lire les caractères à partir du **FileStream**, qui est passé à **StreamReader** en tant qu’argument de son constructeur. Ensuite, <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> lit jusqu’à ce que <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> ne détecte plus aucun caractère.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Exemple : utilisation de BinaryReader
L’exemple suivant crée un <xref:System.IO.BinaryReader> pour lire les octets à partir du **FileStream**, qui est passé à **BinaryReader** en tant qu’argument de son constructeur. Ensuite, <xref:System.IO.BinaryReader.ReadByte%2A> lit jusqu’à ce que <xref:System.IO.BinaryReader.PeekChar%2A> ne détecte plus aucun octet.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
