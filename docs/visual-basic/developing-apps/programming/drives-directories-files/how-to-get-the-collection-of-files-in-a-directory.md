---
title: 'Procédure : placer la collection de fichiers dans un répertoire'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 055151d4b3e3aba6be9b9b03ac9abffc6eb7b734
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401613"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="472ba-102">Guide pratique pour obtenir la collection de fichiers dans un répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="472ba-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="472ba-103">Les surcharges de la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> retournent une collection en lecture seule de chaînes représentant les noms des fichiers contenus dans un répertoire :</span><span class="sxs-lookup"><span data-stu-id="472ba-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="472ba-104">Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> pour effectuer une recherche de fichier simple dans un répertoire spécifié, sans rechercher dans les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="472ba-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="472ba-105">Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> pour spécifier des options supplémentaires pour votre recherche.</span><span class="sxs-lookup"><span data-stu-id="472ba-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="472ba-106">Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="472ba-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="472ba-107">Pour inclure des sous-répertoires dans la recherche, affectez la valeur `searchType` au paramètre <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="472ba-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="472ba-108">Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est détecté.</span><span class="sxs-lookup"><span data-stu-id="472ba-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="472ba-109">Pour énumérer les fichiers contenus dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="472ba-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="472ba-110">Utilisez l'une des surcharges de méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>, en fournissant le nom et le chemin d'accès au répertoire dans lequel effectuer la recherche dans le paramètre `directory`.</span><span class="sxs-lookup"><span data-stu-id="472ba-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="472ba-111">L’exemple suivant retourne tous les fichiers contenus dans le répertoire et les ajoute à `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="472ba-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="472ba-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="472ba-112">Robust Programming</span></span>  

 <span data-ttu-id="472ba-113">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="472ba-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="472ba-114">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="472ba-115">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="472ba-116">`directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="472ba-117">`directory` pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="472ba-118">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="472ba-119">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="472ba-120">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="472ba-121">L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="472ba-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="472ba-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="472ba-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="472ba-123">Procédure : rechercher des fichiers avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="472ba-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="472ba-124">Procédure : rechercher des sous-répertoires avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="472ba-124">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
