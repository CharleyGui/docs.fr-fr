---
title: 'Procédure : rechercher des sous-répertoires avec un modèle spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401626"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="eb3b7-102">Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb3b7-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="eb3b7-103">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des sous-répertoires d’un répertoire.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="eb3b7-104">Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="eb3b7-105">Si vous souhaitez inclure le contenu des sous-répertoires dans la recherche, affectez la valeur `SearchOption.SearchAllSubDirectories` au paramètre `searchType`.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="eb3b7-106">Une collection vide est retournée si aucun répertoire correspondant au modèle spécifié n’est détecté.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="eb3b7-107">Pour rechercher des sous-répertoires avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="eb3b7-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="eb3b7-108">Utilisez la méthode `GetDirectories`, en fournissant le nom et le chemin du répertoire à rechercher.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="eb3b7-109">L’exemple suivant retourne tous les répertoires dans la structure de répertoires dont le nom contient le mot « Logs », et il les ajoute à `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="eb3b7-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="eb3b7-110">Robust Programming</span></span>

<span data-ttu-id="eb3b7-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="eb3b7-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="eb3b7-112">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="eb3b7-113">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="eb3b7-114">Un ou plusieurs des caractères génériques spécifiés sont `Nothing`, une chaîne vide ou contiennent uniquement des espaces (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="eb3b7-115">`directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="eb3b7-116">`directory` pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="eb3b7-117">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="eb3b7-118">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="eb3b7-119">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="eb3b7-120">L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="eb3b7-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb3b7-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb3b7-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="eb3b7-122">Procédure : rechercher des fichiers avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="eb3b7-122">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
