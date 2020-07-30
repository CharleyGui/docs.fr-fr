---
title: Comment lire un fichier texte-Guide de programmation C#
description: Apprenez à lire à partir d’un fichier texte à l’aide de méthodes statiques de la classe file. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301656"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="70907-104">Comment lire un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="70907-104">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="70907-105">Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70907-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="70907-106">Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader> , consultez [Comment lire un fichier texte ligne par ligne](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="70907-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="70907-107">Les fichiers utilisés dans cet exemple sont créés dans la rubrique [Comment écrire dans un fichier texte](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="70907-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="70907-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="70907-108">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70907-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="70907-109">Compiling the Code</span></span>  
 <span data-ttu-id="70907-110">Copiez le code et collez-le dans une application console C#.</span><span class="sxs-lookup"><span data-stu-id="70907-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="70907-111">Si vous n’utilisez pas les fichiers texte à partir de la [procédure d’écriture dans un fichier texte](./how-to-write-to-a-text-file.md), remplacez l’argument par `ReadAllText` et `ReadAllLines` par le chemin d’accès et le nom de fichier appropriés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70907-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="70907-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="70907-112">Robust Programming</span></span>  
 <span data-ttu-id="70907-113">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="70907-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="70907-114">Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="70907-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="70907-115">Vérifiez le chemin et l’orthographe du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="70907-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="70907-116">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="70907-116">.NET Security</span></span>  
 <span data-ttu-id="70907-117">Ne comptez pas sur le nom d’un fichier pour en déduire le contenu.</span><span class="sxs-lookup"><span data-stu-id="70907-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="70907-118">Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="70907-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70907-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70907-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="70907-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="70907-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="70907-121">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="70907-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
