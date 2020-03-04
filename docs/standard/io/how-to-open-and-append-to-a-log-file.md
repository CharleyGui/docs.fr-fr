---
title: 'Procédure : ouvrir un fichier journal et y ajouter des éléments'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155709"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="cf924-102">Procédure : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="cf924-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="cf924-103"><xref:System.IO.StreamWriter> et <xref:System.IO.StreamReader> écrivent des caractères dans et lisent des caractères à partir des flux.</span><span class="sxs-lookup"><span data-stu-id="cf924-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="cf924-104">L’exemple de code suivant ouvre le fichier *log.txt* pour l’entrée, ou crée le fichier s’il n’existe pas déjà, puis ajoute les informations à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="cf924-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="cf924-105">Ensuite, l’exemple écrit le contenu du fichier dans la sortie standard en vue de son affichage.</span><span class="sxs-lookup"><span data-stu-id="cf924-105">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="cf924-106">Comme alternative à cet exemple, vous pourriez stocker les informations dans une chaîne ou un tableau de chaînes, puis utiliser la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ou <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> pour obtenir la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="cf924-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf924-107">Les utilisateurs Visual Basic peuvent choisir d’utiliser les méthodes et les propriétés fournies par la classe <xref:Microsoft.VisualBasic.Logging.Log> ou la classe <xref:Microsoft.VisualBasic.FileIO.FileSystem> pour la création ou l’écriture dans des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="cf924-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf924-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf924-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cf924-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf924-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="cf924-110">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="cf924-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="cf924-111">Comment : lire et écrire dans un fichier de données nouvellement créé</span><span class="sxs-lookup"><span data-stu-id="cf924-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="cf924-112">Comment : lire du texte à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="cf924-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="cf924-113">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="cf924-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="cf924-114">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="cf924-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="cf924-115">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="cf924-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="cf924-116">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="cf924-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
