---
title: 'Procédure : déplacer un fichier dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: e529e263353b08778eba338b20aef34762e66824
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628849"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="4ef21-102">Procédure : déplacer un fichier dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ef21-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="4ef21-103">Vous pouvez utiliser la méthode `My.Computer.FileSystem.MoveFile` pour déplacer un fichier vers un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="4ef21-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="4ef21-104">Si la structure cible n’existe pas, elle est créée.</span><span class="sxs-lookup"><span data-stu-id="4ef21-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="4ef21-105">Pour déplacer un fichier</span><span class="sxs-lookup"><span data-stu-id="4ef21-105">To move a file</span></span>  
  
- <span data-ttu-id="4ef21-106">Utilisez la méthode `MoveFile` pour déplacer le fichier, en spécifiant le nom et l’emplacement du fichier source et du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="4ef21-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="4ef21-107">Dans cet exemple, le fichier nommé `test.txt` est déplacé de `TestDir1` vers `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="4ef21-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="4ef21-108">Notez que le nom du fichier cible est spécifié même s’il est identique à celui du fichier source.</span><span class="sxs-lookup"><span data-stu-id="4ef21-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="4ef21-109">Pour déplacer et renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="4ef21-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="4ef21-110">Utilisez la méthode `MoveFile` pour déplacer le fichier, en spécifiant le nom et l’emplacement du fichier source, l’emplacement cible et le nouveau nom du fichier à l’emplacement cible.</span><span class="sxs-lookup"><span data-stu-id="4ef21-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="4ef21-111">Dans cet exemple, le fichier nommé `test.txt` est déplacé de `TestDir1` vers `TestDir2` , puis renommé en `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="4ef21-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4ef21-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="4ef21-112">Robust Programming</span></span>  
 <span data-ttu-id="4ef21-113">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="4ef21-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4ef21-114">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="4ef21-115">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="4ef21-116">`destinationFileName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="4ef21-117">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="4ef21-118">Le chemin combiné pointe vers un répertoire existant, le fichier de destination existe et `overwrite` a la valeur `False`, un fichier du répertoire cible portant le même nom est actuellement utilisé, ou l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="4ef21-119">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="4ef21-120">`showUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException`et l’utilisateur a annulé l’opération ou une erreur d’E/S non spécifiée s’est produite (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="4ef21-121">Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="4ef21-122">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="4ef21-123">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="4ef21-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef21-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ef21-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="4ef21-125">Guide pratique pour renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="4ef21-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="4ef21-126">Guide pratique pour créer une copie d’un fichier dans un autre répertoire</span><span class="sxs-lookup"><span data-stu-id="4ef21-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="4ef21-127">Guide pratique pour analyser des chemins</span><span class="sxs-lookup"><span data-stu-id="4ef21-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
