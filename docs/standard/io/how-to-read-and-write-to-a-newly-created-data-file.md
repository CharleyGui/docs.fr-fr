---
title: 'Comment : lire et écrire dans un fichier de données nouvellement créé'
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
ms.openlocfilehash: 18f44af81a38a48da3115d2082ef45af39f06529
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291810"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="0ae6a-102">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="0ae6a-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="0ae6a-103">Les classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> et <xref:System.IO.BinaryReader?displayProperty=nameWithType> sont utilisées pour écrire et lire des données autres que des chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="0ae6a-104">L’exemple suivant montre comment créer un flux de fichier vide, y écrire des données, puis les lire.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="0ae6a-105">L’exemple créé un fichier de données appelé *Test.data* dans le répertoire actif, crée les objets <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> associés, puis utilise l’objet <xref:System.IO.BinaryWriter> pour écrire les entiers de 0 à 10 dans *Test.data*, ce qui laisse le pointeur de fichier à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="0ae6a-106">Ensuite, l’objet <xref:System.IO.BinaryReader> replace le pointeur de fichier au début, puis lit le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ae6a-107">Si *Test.data* existe déjà dans le répertoire actif, une exception <xref:System.IO.IOException> est levée.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="0ae6a-108">Utilisez l’option de mode de fichier <xref:System.IO.FileMode.Create?displayProperty=nameWithType> plutôt que <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> pour toujours créer un fichier sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="0ae6a-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae6a-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="0ae6a-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0ae6a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ae6a-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="0ae6a-111">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="0ae6a-111">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="0ae6a-112">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="0ae6a-112">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="0ae6a-113">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="0ae6a-113">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="0ae6a-114">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="0ae6a-114">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="0ae6a-115">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="0ae6a-115">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="0ae6a-116">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="0ae6a-116">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="0ae6a-117">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="0ae6a-117">File and stream I/O</span></span>](index.md)
