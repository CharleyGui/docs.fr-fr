---
title: "Comment : écrire du texte dans des fichiers à l'aide de Streamwriter"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334495"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="73900-102">Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73900-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="73900-103">Cet exemple ouvre un objet <xref:System.IO.StreamWriter> avec la méthode `My.Computer.FileSystem.OpenTextFileWriter` et l’utilise pour écrire une chaîne dans un fichier texte avec la méthode <xref:System.IO.TextWriter.WriteLine%2A> de la classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="73900-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73900-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="73900-104">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="73900-105">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="73900-105">Robust Programming</span></span>  

 <span data-ttu-id="73900-106">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="73900-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="73900-107">Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="73900-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="73900-108">Le disque est plein (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="73900-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="73900-109">Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="73900-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="73900-110">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="73900-110">.NET Framework Security</span></span>  

 <span data-ttu-id="73900-111">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="73900-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="73900-112">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="73900-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="73900-113">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="73900-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="73900-114">Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="73900-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73900-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73900-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="73900-116">Guide pratique pour lire des fichiers texte</span><span class="sxs-lookup"><span data-stu-id="73900-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="73900-117">Rédaction de fichiers</span><span class="sxs-lookup"><span data-stu-id="73900-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
