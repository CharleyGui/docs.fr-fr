---
title: Guide pratique pour compresser et extraire des fichiers
description: Compressez les fichiers d’extraction & à l’aide de System. IO. compression. Consultez les exemples utilisant ZipFile, ZipArchive, ZipArchiveEntry, DeflateStream, & GZipStream.
ms.date: 01/14/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: a1077c7277e0aa54e3c8883cfc27d93926485b8e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830855"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="e6b07-104">Guide pratique pour compresser et extraire des fichiers</span><span class="sxs-lookup"><span data-stu-id="e6b07-104">How to: Compress and extract files</span></span>

<span data-ttu-id="e6b07-105">L'espace de noms <xref:System.IO.Compression> contient les types suivants pour la compression et la décompression de fichiers et de flux.</span><span class="sxs-lookup"><span data-stu-id="e6b07-105">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="e6b07-106">Vous pouvez également utiliser ces types pour lire et modifier le contenu d’un fichier compressé.</span><span class="sxs-lookup"><span data-stu-id="e6b07-106">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="e6b07-107">Les exemples suivants présentent certaines des opérations que vous pouvez effectuer avec des fichiers compressés.</span><span class="sxs-lookup"><span data-stu-id="e6b07-107">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="e6b07-108">Ces exemples nécessitent l’ajout des packages NuGet suivants à votre projet :</span><span class="sxs-lookup"><span data-stu-id="e6b07-108">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="e6b07-109">System.IO.Compression</span><span class="sxs-lookup"><span data-stu-id="e6b07-109">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="e6b07-110">System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="e6b07-110">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="e6b07-111">Si vous utilisez .NET Framework, ajoutez des références à ces deux bibliothèques à votre projet :</span><span class="sxs-lookup"><span data-stu-id="e6b07-111">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="e6b07-112">Exemple 1 : créer et extraire un fichier. zip</span><span class="sxs-lookup"><span data-stu-id="e6b07-112">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="e6b07-113">L’exemple suivant montre comment créer et extraire un fichier *.zip* à l’aide de la classe <xref:System.IO.Compression.ZipFile>.</span><span class="sxs-lookup"><span data-stu-id="e6b07-113">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="e6b07-114">Cet exemple compresse le contenu d’un dossier dans un nouveau fichier *.zip*, puis extrait ce fichier zip dans un nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="e6b07-114">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="e6b07-115">Pour exécuter l’exemple, créez un dossier *start* dans le dossier de votre programme, puis placez-y les fichiers à compresser.</span><span class="sxs-lookup"><span data-stu-id="e6b07-115">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="e6b07-116">Exemple 2 : extraire des extensions de fichier spécifiques</span><span class="sxs-lookup"><span data-stu-id="e6b07-116">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="e6b07-117">L’exemple suivant montre comment parcourir le contenu d’un fichier *.zip* existant et en extraire les fichiers ayant une extension *.txt*.</span><span class="sxs-lookup"><span data-stu-id="e6b07-117">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="e6b07-118">Il utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder au fichier zip, et la classe <xref:System.IO.Compression.ZipArchiveEntry> pour inspecter chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="e6b07-118">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="e6b07-119">La méthode d’extension <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> de l’objet <xref:System.IO.Compression.ZipArchiveEntry> est disponible dans la classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6b07-119">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="e6b07-120">Pour exécuter l’exemple, placez un fichier *.zip* appelé *result.zip* dans le dossier de votre programme.</span><span class="sxs-lookup"><span data-stu-id="e6b07-120">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="e6b07-121">Lorsque vous y êtes invité, fournissez le nom du dossier vers lequel extraire les fichiers.</span><span class="sxs-lookup"><span data-stu-id="e6b07-121">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6b07-122">Lors de la décompression des fichiers, vous devez rechercher les chemins malveillants qui risquent d’extraire les fichiers en dehors du répertoire.</span><span class="sxs-lookup"><span data-stu-id="e6b07-122">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="e6b07-123">Il s’agit d’une attaque par chemin transversal.</span><span class="sxs-lookup"><span data-stu-id="e6b07-123">This is known as a path traversal attack.</span></span> <span data-ttu-id="e6b07-124">L’exemple suivant montre comment rechercher les chemins malveillants et garantir une décompression sûre.</span><span class="sxs-lookup"><span data-stu-id="e6b07-124">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="e6b07-125">Exemple 3 : ajouter un fichier à un fichier zip existant</span><span class="sxs-lookup"><span data-stu-id="e6b07-125">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="e6b07-126">L’exemple suivant utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder à un fichier *.zip* existant, et y ajouter un fichier.</span><span class="sxs-lookup"><span data-stu-id="e6b07-126">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="e6b07-127">Le nouveau fichier est compressé quand vous l’ajoutez au fichier zip existant.</span><span class="sxs-lookup"><span data-stu-id="e6b07-127">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="e6b07-128">Exemple 4 : compresser et décompresser les fichiers. gz</span><span class="sxs-lookup"><span data-stu-id="e6b07-128">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="e6b07-129">Vous pouvez également utiliser les classes <xref:System.IO.Compression.GZipStream> et <xref:System.IO.Compression.DeflateStream> pour compresser et décompresser des données.</span><span class="sxs-lookup"><span data-stu-id="e6b07-129">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="e6b07-130">Elles utilisent le même algorithme de compression.</span><span class="sxs-lookup"><span data-stu-id="e6b07-130">They use the same compression algorithm.</span></span> <span data-ttu-id="e6b07-131">Vous pouvez décompresser les objets <xref:System.IO.Compression.GZipStream> qui sont écrits dans un fichier *.gz* à l’aide de nombreux outils courants.</span><span class="sxs-lookup"><span data-stu-id="e6b07-131">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="e6b07-132">L’exemple suivant montre comment compresser et décompresser un répertoire de fichiers à l’aide de la classe <xref:System.IO.Compression.GZipStream> :</span><span class="sxs-lookup"><span data-stu-id="e6b07-132">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e6b07-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6b07-133">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="e6b07-134">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="e6b07-134">File and stream I/O</span></span>](index.md)
