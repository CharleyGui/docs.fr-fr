---
title: 'Comment : lire et écrire des fichiers dans un stockage isolé'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: a1ea65b0b8280faf51595b2fe9edcbf17eaabd8f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706684"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Comment : lire et écrire des fichiers dans un stockage isolé
Pour lire ou écrire dans un fichier dans un magasin isolé, utilisez un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> avec un lecteur de flux (objet <xref:System.IO.StreamReader>) ou un writer de flux (objet <xref:System.IO.StreamWriter>).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant obtient un magasin isolé et vérifie l’existence d’un fichier intitulé TestStore.txt dans le magasin. S’il n’existe pas, il crée le fichier et écrit « Hello Isolated Storage » dans le fichier. Si TestStore.txt existe déjà, l’exemple de code lit le fichier.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
- [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
