---
title: 'Procédure : supprimer un fichier'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 0c8213786b8073d784f1f3ea51417741d5ad4cba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401652"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="0877a-102">Guide pratique pour supprimer un fichier dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0877a-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="0877a-103">La méthode `DeleteFile` de l’objet `My.Computer.FileSystem` vous permet de supprimer un fichier.</span><span class="sxs-lookup"><span data-stu-id="0877a-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="0877a-104">Elle offre entre autres les options suivantes : envoyer ou non le fichier supprimé à la **Corbeille**, demander ou non à l’utilisateur de confirmer que le fichier doit être supprimé et l’action à effectuer quand l’utilisateur annule l’opération.</span><span class="sxs-lookup"><span data-stu-id="0877a-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="0877a-105">Pour supprimer un fichier texte</span><span class="sxs-lookup"><span data-stu-id="0877a-105">To delete a text file</span></span>  
  
- <span data-ttu-id="0877a-106">Utilisez la méthode `DeleteFile` pour supprimer le fichier.</span><span class="sxs-lookup"><span data-stu-id="0877a-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="0877a-107">Le code suivant illustre comment supprimer le fichier nommé `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="0877a-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="0877a-108">Pour supprimer un fichier texte et demander à l’utilisateur de confirmer que le fichier doit être supprimé</span><span class="sxs-lookup"><span data-stu-id="0877a-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="0877a-109">Utilisez la méthode `DeleteFile` pour supprimer le fichier en affectant `showUI` à `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="0877a-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="0877a-110">Le code suivant illustre comment supprimer le fichier nommé `test.txt` et permettre à l’utilisateur de confirmer que le fichier doit être supprimé.</span><span class="sxs-lookup"><span data-stu-id="0877a-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="0877a-111">Pour supprimer un fichier texte et l’envoyer à la Corbeille</span><span class="sxs-lookup"><span data-stu-id="0877a-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="0877a-112">Utilisez la méthode `DeleteFile` pour supprimer le fichier en spécifiant `SendToRecycleBin` pour le paramètre `recycle`.</span><span class="sxs-lookup"><span data-stu-id="0877a-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="0877a-113">Le code suivant illustre comment supprimer le fichier nommé `test.txt` et l’envoyer à la **Corbeille**.</span><span class="sxs-lookup"><span data-stu-id="0877a-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0877a-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="0877a-114">Robust Programming</span></span>  

 <span data-ttu-id="0877a-115">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="0877a-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0877a-116">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0877a-117">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0877a-118">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0877a-119">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0877a-120">Le fichier est en cours d’utilisation (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0877a-121">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0877a-122">Le fichier n'existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="0877a-123">L’utilisateur n’a pas l’autorisation de supprimer le fichier ou le fichier est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="0877a-124">Une situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes existe (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0877a-125">L’utilisateur a annulé l’opération et `onUserCancel` a la valeur `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="0877a-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0877a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0877a-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="0877a-127">Procédure : placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="0877a-127">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
