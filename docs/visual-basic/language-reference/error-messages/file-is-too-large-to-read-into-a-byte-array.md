---
title: Le fichier est trop volumineux pour être lu dans un tableau d'octets
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363122"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="2ce0b-102">Le fichier est trop volumineux pour être lu dans un tableau d'octets</span><span class="sxs-lookup"><span data-stu-id="2ce0b-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="2ce0b-103">La taille du fichier que vous tentez de lire dans un tableau d’octets dépasse 4 Go.</span><span class="sxs-lookup"><span data-stu-id="2ce0b-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="2ce0b-104">La `My.Computer.FileSystem.ReadAllBytes` méthode ne peut pas lire un fichier qui dépasse cette taille.</span><span class="sxs-lookup"><span data-stu-id="2ce0b-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ce0b-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2ce0b-105">To correct this error</span></span>  
  
- <span data-ttu-id="2ce0b-106">Utilisez un <xref:System.IO.StreamReader> pour lire le fichier.</span><span class="sxs-lookup"><span data-stu-id="2ce0b-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="2ce0b-107">Pour plus d’informations, consultez [principes de base de l’e/s de fichier .NET Framework et du système de fichiers (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="2ce0b-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce0b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ce0b-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="2ce0b-109">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ce0b-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="2ce0b-110">Procédure : lire du texte à partir de fichiers avec un StreamReader</span><span class="sxs-lookup"><span data-stu-id="2ce0b-110">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
