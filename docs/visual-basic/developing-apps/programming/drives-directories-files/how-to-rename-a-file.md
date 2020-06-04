---
title: 'Procédure : renommer un fichier'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411588"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="754b6-102">Guide pratique pour renommer un fichier en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="754b6-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="754b6-103">Utilisez la méthode `RenameFile` de l’objet `My.Computer.FileSystem` pour renommer un fichier en fournissant l’emplacement actuel, le nom actuel du fichier et le nouveau nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="754b6-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="754b6-104">Cette méthode ne peut pas être utilisée pour déplacer un fichier. Utilisez la méthode `MoveFile` pour déplacer et renommer le fichier.</span><span class="sxs-lookup"><span data-stu-id="754b6-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="754b6-105">Pour renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="754b6-105">To rename a file</span></span>  
  
- <span data-ttu-id="754b6-106">Pour renommer un fichier, utilisez la méthode `My.Computer.FileSystem.RenameFile`.</span><span class="sxs-lookup"><span data-stu-id="754b6-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="754b6-107">Dans cet exemple, le nom de fichier `Test.txt` est remplacé par `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="754b6-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="754b6-108">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="754b6-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="754b6-109">Dans le sélecteur d’extraits de code, il se trouve dans **Système de fichiers - Traitement des lecteurs, dossiers et fichiers**.</span><span class="sxs-lookup"><span data-stu-id="754b6-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="754b6-110">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="754b6-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="754b6-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="754b6-111">Robust Programming</span></span>  

 <span data-ttu-id="754b6-112">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="754b6-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="754b6-113">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="754b6-114">`newName` contient des informations de chemin (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="754b6-115">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="754b6-116">`newName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="754b6-117">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="754b6-118">Un fichier ou un répertoire porte déjà le nom spécifié dans `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="754b6-119">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="754b6-120">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="754b6-121">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="754b6-122">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="754b6-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754b6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="754b6-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="754b6-124">Procédure : déplacer un fichier</span><span class="sxs-lookup"><span data-stu-id="754b6-124">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="754b6-125">Création, suppression et déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="754b6-125">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="754b6-126">Procédure : créer une copie d’un fichier dans le même répertoire</span><span class="sxs-lookup"><span data-stu-id="754b6-126">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="754b6-127">Procédure : créer une copie d’un fichier dans un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="754b6-127">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
