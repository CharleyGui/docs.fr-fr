---
title: 'Procédure : ouvrir un fichier journal et y ajouter des éléments'
description: Ouvrez et ajoutez à un fichier journal à l’aide des classes StreamWriter et StreamReader dans .NET, qui écrivent des caractères dans les flux et les lisent.
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: be4cacee8d0a529730c66c5850f42330520ba2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734606"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="bd0ca-103">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="bd0ca-103">How to: Open and append to a log file</span></span>

<span data-ttu-id="bd0ca-104"><xref:System.IO.StreamWriter> et <xref:System.IO.StreamReader> écrivent des caractères dans et lisent des caractères à partir des flux.</span><span class="sxs-lookup"><span data-stu-id="bd0ca-104"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="bd0ca-105">L’exemple de code suivant ouvre le fichier *log.txt* pour l’entrée, ou crée le fichier s’il n’existe pas déjà, puis ajoute les informations à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="bd0ca-105">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="bd0ca-106">Ensuite, l’exemple écrit le contenu du fichier dans la sortie standard en vue de son affichage.</span><span class="sxs-lookup"><span data-stu-id="bd0ca-106">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="bd0ca-107">Comme alternative à cet exemple, vous pourriez stocker les informations dans une chaîne ou un tableau de chaînes, puis utiliser la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ou <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> pour obtenir la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="bd0ca-107">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd0ca-108">Les utilisateurs Visual Basic peuvent choisir d’utiliser les méthodes et les propriétés fournies par la classe <xref:Microsoft.VisualBasic.Logging.Log> ou la classe <xref:Microsoft.VisualBasic.FileIO.FileSystem> pour la création ou l’écriture dans des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="bd0ca-108">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd0ca-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd0ca-109">Example</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bd0ca-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd0ca-110">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="bd0ca-111">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="bd0ca-111">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="bd0ca-112">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="bd0ca-112">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="bd0ca-113">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="bd0ca-113">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="bd0ca-114">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="bd0ca-114">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="bd0ca-115">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="bd0ca-115">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="bd0ca-116">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="bd0ca-116">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="bd0ca-117">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="bd0ca-117">File and stream I/O</span></span>](index.md)
