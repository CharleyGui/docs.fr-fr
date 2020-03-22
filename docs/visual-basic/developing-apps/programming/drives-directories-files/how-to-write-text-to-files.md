---
title: 'Comment : insérer du texte dans des fichiers'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334470"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="f089b-102">Guide pratique pour écrire du texte dans des fichiers en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f089b-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="f089b-103">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pour écrire du texte dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="f089b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="f089b-104">Si le fichier spécifié n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="f089b-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="f089b-105">Procédure</span><span class="sxs-lookup"><span data-stu-id="f089b-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="f089b-106">Pour écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="f089b-106">To write text to a file</span></span>  
  
- <span data-ttu-id="f089b-107">Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier et le texte à écrire.</span><span class="sxs-lookup"><span data-stu-id="f089b-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="f089b-108">Cet exemple écrit la ligne `"This is new text."` dans le fichier nommé `test.txt`. Le texte est ajouté au texte existant dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f089b-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="f089b-109">Pour écrire une série de chaînes dans un fichier</span><span class="sxs-lookup"><span data-stu-id="f089b-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="f089b-110">Parcourez la collection de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f089b-110">Loop through the string collection.</span></span> <span data-ttu-id="f089b-111">Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier, en spécifiant le fichier cible et la chaîne à ajouter, puis en affectant la valeur `True` au paramètre `append`.</span><span class="sxs-lookup"><span data-stu-id="f089b-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="f089b-112">Cet exemple écrit les noms des fichiers dans le répertoire `Documents and Settings` dans `FileList.txt`, et insère un retour chariot entre chacun d’eux pour une meilleure lisibilité.</span><span class="sxs-lookup"><span data-stu-id="f089b-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f089b-113">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="f089b-113">Robust Programming</span></span>  

 <span data-ttu-id="f089b-114">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="f089b-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f089b-115">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f089b-116">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f089b-117">`File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f089b-118">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f089b-119">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f089b-120">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="f089b-121">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="f089b-122">Le disque est plein et l’appel à `WriteAllText` échoue (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f089b-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="f089b-123">Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="f089b-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f089b-124">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="f089b-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f089b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f089b-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="f089b-126">Guide pratique pour lire des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="f089b-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
