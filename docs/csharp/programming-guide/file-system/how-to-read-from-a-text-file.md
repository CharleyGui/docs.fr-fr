---
title: Comment lire un fichier texte-Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 8f79d22a86390ca931b05262e50865d852c154c7
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241745"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="2d083-102">Comment lire un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2d083-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="2d083-103">Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d083-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="2d083-104">Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader> , consultez [Comment lire un fichier texte ligne par ligne](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="2d083-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2d083-105">Les fichiers utilisés dans cet exemple sont créés dans la rubrique [Comment écrire dans un fichier texte](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="2d083-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="2d083-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d083-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d083-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2d083-107">Compiling the Code</span></span>  
 <span data-ttu-id="2d083-108">Copiez le code et collez-le dans une application console C#.</span><span class="sxs-lookup"><span data-stu-id="2d083-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="2d083-109">Si vous n’utilisez pas les fichiers texte à partir de la [procédure d’écriture dans un fichier texte](./how-to-write-to-a-text-file.md), remplacez l’argument par `ReadAllText` et `ReadAllLines` par le chemin d’accès et le nom de fichier appropriés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2d083-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="2d083-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="2d083-110">Robust Programming</span></span>  
 <span data-ttu-id="2d083-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="2d083-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2d083-112">Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="2d083-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="2d083-113">Vérifiez le chemin et l’orthographe du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="2d083-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="2d083-114">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="2d083-114">.NET Security</span></span>  
 <span data-ttu-id="2d083-115">Ne comptez pas sur le nom d’un fichier pour en déduire le contenu.</span><span class="sxs-lookup"><span data-stu-id="2d083-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="2d083-116">Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="2d083-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d083-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d083-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="2d083-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2d083-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2d083-119">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2d083-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
