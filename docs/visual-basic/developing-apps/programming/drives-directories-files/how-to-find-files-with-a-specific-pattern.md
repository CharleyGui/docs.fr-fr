---
title: 'Comment : rechercher des fichiers avec un modèle spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348759"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="a5f1a-102">Guide pratique pour rechercher des fichiers avec un modèle spécifique en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5f1a-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="a5f1a-103">La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="a5f1a-104">Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="a5f1a-105">Si vous voulez inclure des sous-répertoires dans la recherche, affectez la valeur `SearchOption.SearchAllSubDirectories` au paramètre `searchType`.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="a5f1a-106">Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est détecté.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5f1a-107">Pour plus d’informations sur la façon de retourner une liste de fichiers à l’aide de la classe `DirectoryInfo` de l’espace de noms `System.IO`, consultez <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="a5f1a-108">Pour rechercher des fichiers avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="a5f1a-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="a5f1a-109">Utilisez la méthode `GetFiles`, en fournissant le nom et le chemin du répertoire à rechercher et en spécifiant le modèle.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="a5f1a-110">L’exemple suivant retourne tous les fichiers ayant l’extension `.dll` contenus dans le répertoire, et il les ajoute à `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="a5f1a-111">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5f1a-111">.NET Framework Security</span></span>  

 <span data-ttu-id="a5f1a-112">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="a5f1a-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a5f1a-113">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="a5f1a-114">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="a5f1a-115">`directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="a5f1a-116">`directory` pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="a5f1a-117">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="a5f1a-118">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="a5f1a-119">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="a5f1a-120">L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="a5f1a-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f1a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5f1a-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="a5f1a-122">Comment : rechercher des sous-répertoires avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="a5f1a-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="a5f1a-123">Dépannage : lecture et écriture dans des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="a5f1a-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="a5f1a-124">Comment : placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="a5f1a-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
