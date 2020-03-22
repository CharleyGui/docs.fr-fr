---
title: "Comment : créer une copie d'un fichier dans le même répertoire"
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348823"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="70038-102">Guide pratique pour créer une copie d'un fichier dans le même répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70038-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="70038-103">Utilisez la méthode `My.Computer.FileSystem.CopyFile` pour copier des fichiers.</span><span class="sxs-lookup"><span data-stu-id="70038-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="70038-104">Les paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d’afficher la progression de l’opération et d’autoriser l’utilisateur à annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="70038-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="70038-105">Pour créer une copie d’un fichier dans le même dossier</span><span class="sxs-lookup"><span data-stu-id="70038-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="70038-106">Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="70038-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="70038-107">L’exemple suivant crée une copie de `test.txt` nommée `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="70038-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="70038-108">Pour créer une copie d’un fichier dans le même dossier en remplaçant les fichiers existants</span><span class="sxs-lookup"><span data-stu-id="70038-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="70038-109">Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement, et en affectant la valeur `True` à `overwrite`.</span><span class="sxs-lookup"><span data-stu-id="70038-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="70038-110">L’exemple suivant crée une copie de `test.txt` nommée `test2.txt` et remplace les fichiers existants portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="70038-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="70038-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="70038-111">Robust Programming</span></span>  

 <span data-ttu-id="70038-112">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="70038-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="70038-113">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="70038-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="70038-114">Le système n’a pas pu récupérer le chemin absolu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="70038-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="70038-115">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="70038-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="70038-116">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="70038-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="70038-117">Le chemin combiné pointe vers un répertoire existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="70038-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="70038-118">Le fichier de destination existe et `overwrite` a la valeur `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="70038-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="70038-119">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="70038-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="70038-120">Un fichier du même nom dans le dossier cible est en cours d’utilisation (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="70038-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="70038-121">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="70038-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="70038-122">`ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l’utilisateur a annulé l’opération (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="70038-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="70038-123">`ShowUI`a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur d’E/S non spécifiée se produit (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="70038-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="70038-124">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="70038-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="70038-125">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="70038-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="70038-126">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="70038-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70038-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70038-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="70038-128">Comment : copier des fichiers avec un modèle spécifique dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="70038-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="70038-129">Comment : créer une copie d'un fichier dans un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="70038-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="70038-130">Comment : copier un répertoire vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="70038-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="70038-131">Comment : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="70038-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
