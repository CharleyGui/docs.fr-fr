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
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 9a6b2985b7f532476c0f4c0f998d710f95e55d3a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769156"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="b95bb-103">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="b95bb-103">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="b95bb-104">Les classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> et <xref:System.IO.BinaryReader?displayProperty=nameWithType> sont utilisées pour écrire et lire des données autres que des chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="b95bb-104">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="b95bb-105">L’exemple suivant montre comment créer un flux de fichier vide, y écrire des données, puis les lire.</span><span class="sxs-lookup"><span data-stu-id="b95bb-105">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="b95bb-106">L’exemple créé un fichier de données appelé *Test.data* dans le répertoire actif, crée les objets <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> associés, puis utilise l’objet <xref:System.IO.BinaryWriter> pour écrire les entiers de 0 à 10 dans *Test.data*, ce qui laisse le pointeur de fichier à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="b95bb-106">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="b95bb-107">Ensuite, l’objet <xref:System.IO.BinaryReader> replace le pointeur de fichier au début, puis lit le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="b95bb-107">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b95bb-108">Si *Test.data* existe déjà dans le répertoire actif, une exception <xref:System.IO.IOException> est levée.</span><span class="sxs-lookup"><span data-stu-id="b95bb-108">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="b95bb-109">Utilisez l’option de mode de fichier <xref:System.IO.FileMode.Create?displayProperty=nameWithType> plutôt que <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> pour toujours créer un fichier sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="b95bb-109">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b95bb-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b95bb-110">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b95bb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b95bb-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="b95bb-112">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="b95bb-112">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="b95bb-113">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="b95bb-113">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="b95bb-114">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="b95bb-114">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="b95bb-115">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="b95bb-115">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="b95bb-116">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="b95bb-116">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="b95bb-117">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="b95bb-117">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="b95bb-118">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="b95bb-118">File and stream I/O</span></span>](index.md)
