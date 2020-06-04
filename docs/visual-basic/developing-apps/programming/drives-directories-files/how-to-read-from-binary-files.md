---
title: 'Procédure : lire des fichiers binaires'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359927"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="efadb-102">Guide pratique pour lire des fichiers binaires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efadb-102">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="efadb-103">L’objet `My.Computer.FileSystem` fournit la méthode `ReadAllBytes` pour la lecture de fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="efadb-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="efadb-104">Pour lire un fichier binaire</span><span class="sxs-lookup"><span data-stu-id="efadb-104">To read from a binary file</span></span>  
  
- <span data-ttu-id="efadb-105">Utilisez la méthode `ReadAllBytes`, qui retourne le contenu d’un fichier en tant que tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="efadb-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="efadb-106">Cet exemple lit le fichier `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="efadb-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="efadb-107">Pour les fichiers binaires volumineux, vous pouvez utiliser la méthode <xref:System.IO.FileStream.Read%2A> de l’objet <xref:System.IO.FileStream> pour lire le fichier bloc par bloc.</span><span class="sxs-lookup"><span data-stu-id="efadb-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="efadb-108">Vous pouvez alors limiter la quantité de données du fichier chargées en mémoire pour chaque opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="efadb-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="efadb-109">L’exemple de code suivant copie un fichier et permet à l’appelant de spécifier la quantité de données lues en mémoire pour chaque opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="efadb-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="efadb-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="efadb-110">Robust Programming</span></span>  

 <span data-ttu-id="efadb-111">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="efadb-111">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="efadb-112">Le chemin d'accès n'est pas valide pour une des raisons suivantes : il s'agit d'une chaîne de longueur nulle ; il ne contient que des espaces blancs ; il contient des caractères non valides ou il s'agit d'un chemin d'accès de périphérique (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="efadb-113">Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="efadb-114">Le fichier n'existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="efadb-115">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="efadb-116">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="efadb-117">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="efadb-118">Il n'y a pas assez de mémoire pour écrire la chaîne dans la mémoire tampon (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="efadb-119">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="efadb-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="efadb-120">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="efadb-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="efadb-121">Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efadb-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="efadb-122">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="efadb-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="efadb-123">Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="efadb-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efadb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efadb-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="efadb-125">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="efadb-125">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="efadb-126">Procédure : lire des fichiers texte avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="efadb-126">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="efadb-127">Stockage de données dans le Presse-papiers et lecture du Presse-papiers</span><span class="sxs-lookup"><span data-stu-id="efadb-127">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
