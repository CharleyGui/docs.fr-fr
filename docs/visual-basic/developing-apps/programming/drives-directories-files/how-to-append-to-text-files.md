---
title: 'Comment : effectuer un ajout à des fichiers texte'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348872"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="79c95-102">Guide pratique pour effectuer un ajout à des fichiers texte en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79c95-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="79c95-103">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pour ajouter un fichier texte en spécifiant que le paramètre `append` est défini avec la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="79c95-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="79c95-104">Pour effectuer un ajout à un fichier texte</span><span class="sxs-lookup"><span data-stu-id="79c95-104">To append to a text file</span></span>  
  
- <span data-ttu-id="79c95-105">Utilisez la méthode `WriteAllText`, en spécifiant le fichier cible et la chaîne à ajouter, et en affectant la valeur `True` au paramètre `append`.</span><span class="sxs-lookup"><span data-stu-id="79c95-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="79c95-106">Cet exemple écrit la chaîne `"This is a test string."` dans le fichier nommé `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="79c95-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="79c95-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="79c95-107">Robust Programming</span></span>  

 <span data-ttu-id="79c95-108">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="79c95-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="79c95-109">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="79c95-110">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="79c95-111">`File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="79c95-112">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="79c95-113">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="79c95-114">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="79c95-115">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="79c95-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c95-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79c95-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="79c95-117">Rédaction de fichiers</span><span class="sxs-lookup"><span data-stu-id="79c95-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
