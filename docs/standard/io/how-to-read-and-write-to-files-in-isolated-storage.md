---
title: 'Procédure : lire et écrire des fichiers dans un stockage isolé'
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
ms.openlocfilehash: d0c95f418ff85654dceed296b7a891c025ab2e62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291797"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="ce85f-102">Procédure : lire et écrire des fichiers dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="ce85f-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="ce85f-103">Pour lire ou écrire dans un fichier dans un magasin isolé, utilisez un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> avec un lecteur de flux (objet <xref:System.IO.StreamReader>) ou un writer de flux (objet <xref:System.IO.StreamWriter>).</span><span class="sxs-lookup"><span data-stu-id="ce85f-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce85f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce85f-104">Example</span></span>  
 <span data-ttu-id="ce85f-105">L’exemple de code suivant obtient un magasin isolé et vérifie l’existence d’un fichier intitulé TestStore.txt dans le magasin.</span><span class="sxs-lookup"><span data-stu-id="ce85f-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="ce85f-106">S’il n’existe pas, il crée le fichier et écrit « Hello Isolated Storage » dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="ce85f-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="ce85f-107">Si TestStore.txt existe déjà, l’exemple de code lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="ce85f-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ce85f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce85f-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="ce85f-109">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="ce85f-109">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="ce85f-110">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="ce85f-110">Isolated Storage</span></span>](isolated-storage.md)
