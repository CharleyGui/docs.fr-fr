---
title: 'Procédure : écrire dans des fichiers binaires'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: b36da82060b930101cb54dd852d050ac0155bd10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411549"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="b78bb-102">Guide pratique pour écrire dans des fichiers binaires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b78bb-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="b78bb-103">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> écrit des données dans un fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="b78bb-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="b78bb-104">Si le paramètre `append` est `True`, elle ajoute les données au fichier ; sinon, les données dans le fichier sont remplacées.</span><span class="sxs-lookup"><span data-stu-id="b78bb-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="b78bb-105">Si le chemin spécifié (nom de fichier exclu) n’est pas valide, une exception <xref:System.IO.DirectoryNotFoundException> est levée.</span><span class="sxs-lookup"><span data-stu-id="b78bb-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="b78bb-106">Si le chemin est valide mais que le fichier n’existe pas, le fichier est créé.</span><span class="sxs-lookup"><span data-stu-id="b78bb-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="b78bb-107">Pour écrire dans un fichier binaire</span><span class="sxs-lookup"><span data-stu-id="b78bb-107">To write to a binary file</span></span>

<span data-ttu-id="b78bb-108">Utilisez la méthode `WriteAllBytes` en fournissant le chemin et le nom du fichier, ainsi que les octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="b78bb-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="b78bb-109">Cet exemple ajoute le tableau de données `CustomerData` au fichier nommé `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="b78bb-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="b78bb-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="b78bb-110">Robust Programming</span></span>

<span data-ttu-id="b78bb-111">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="b78bb-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="b78bb-112">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs ou il contient des caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="b78bb-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="b78bb-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="b78bb-114">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="b78bb-115">`File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="b78bb-116">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="b78bb-117">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="b78bb-118">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="b78bb-119">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b78bb-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="b78bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b78bb-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="b78bb-121">Procédure : écrire du texte dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="b78bb-121">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
