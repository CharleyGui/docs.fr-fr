---
title: "Comment : créer une copie d'un fichier dans un autre répertoire"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348832"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="ada73-102">Guide pratique pour créer une copie d'un fichier dans un autre répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ada73-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="ada73-103">La méthode `My.Computer.FileSystem.CopyFile` permet de copier des fichiers.</span><span class="sxs-lookup"><span data-stu-id="ada73-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="ada73-104">Ses paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d’afficher la progression de l’opération et d’autoriser l’utilisateur à annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="ada73-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="ada73-105">Pour copier un fichier texte dans un autre dossier</span><span class="sxs-lookup"><span data-stu-id="ada73-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="ada73-106">Utilisez la méthode `CopyFile` pour copier un fichier, en spécifiant un fichier source et le répertoire cible.</span><span class="sxs-lookup"><span data-stu-id="ada73-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="ada73-107">Le paramètre `overwrite` permet de spécifier s’il faut remplacer les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="ada73-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="ada73-108">Les exemples de code suivants illustrent comment utiliser `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="ada73-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ada73-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ada73-109">Robust Programming</span></span>  

 <span data-ttu-id="ada73-110">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="ada73-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="ada73-111">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ada73-112">Le système n’a pas pu récupérer le chemin absolu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ada73-113">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="ada73-114">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="ada73-115">Le chemin combiné pointe vers un répertoire existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ada73-116">Le fichier de destination existe et `overwrite` a la valeur `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ada73-117">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ada73-118">Un fichier du même nom dans le dossier cible est en cours d’utilisation (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ada73-119">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="ada73-120">`ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l’utilisateur a annulé l’opération (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="ada73-121">`ShowUI`a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur d’E/S non spécifiée se produit (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="ada73-122">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ada73-123">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="ada73-124">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ada73-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada73-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ada73-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="ada73-126">Comment : copier des fichiers avec un modèle spécifique dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="ada73-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="ada73-127">Comment : créer une copie d'un fichier dans le même répertoire</span><span class="sxs-lookup"><span data-stu-id="ada73-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="ada73-128">Comment : copier un répertoire vers un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="ada73-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="ada73-129">Comment : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="ada73-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
