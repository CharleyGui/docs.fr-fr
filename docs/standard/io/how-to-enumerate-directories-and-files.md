---
title: 'Comment : énumérer des répertoires et des fichiers'
description: Apprenez à énumérer des répertoires et des fichiers à l’aide de collections énumérables, qui peuvent fournir de meilleures performances que les tableaux dans .NET.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 276668f4a3eee89610a81b1256820770d1f72dc3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662574"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="6fb51-103">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="6fb51-103">How to: Enumerate directories and files</span></span>
<span data-ttu-id="6fb51-104">Les collections énumérables offrent de meilleures performances que les tableaux lorsque vous travaillez avec collections volumineuses de fichiers et de répertoires.</span><span class="sxs-lookup"><span data-stu-id="6fb51-104">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="6fb51-105">Pour énumérer des répertoires et des fichiers, utilisez des méthodes qui retournent une collection énumérable de noms de répertoire ou de fichier ou leurs objets <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> ou <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="6fb51-105">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="6fb51-106">Si vous souhaitez parcourir et retourner uniquement les noms des répertoires ou des fichiers, utilisez les méthodes d’énumération de la classe <xref:System.IO.Directory>.</span><span class="sxs-lookup"><span data-stu-id="6fb51-106">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="6fb51-107">Si vous souhaitez parcourir et retourner d’autres propriétés des répertoires ou des fichiers, utilisez les classes <xref:System.IO.DirectoryInfo> et <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="6fb51-107">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="6fb51-108">Vous pouvez utiliser les collections énumérables issues de ces méthodes en tant que paramètre <xref:System.Collections.Generic.IEnumerable%601> pour les constructeurs de classes de collection, comme <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="6fb51-108">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="6fb51-109">Le tableau suivant récapitule les méthodes qui retournent des collections énumérables de fichiers et de répertoires .</span><span class="sxs-lookup"><span data-stu-id="6fb51-109">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="6fb51-110">Pour parcourir et retourner</span><span class="sxs-lookup"><span data-stu-id="6fb51-110">To search and return</span></span>|<span data-ttu-id="6fb51-111">Utiliser la méthode</span><span class="sxs-lookup"><span data-stu-id="6fb51-111">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="6fb51-112">Noms de répertoires</span><span class="sxs-lookup"><span data-stu-id="6fb51-112">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-113">Informations sur le répertoire (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="6fb51-113">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-114">Noms de fichiers</span><span class="sxs-lookup"><span data-stu-id="6fb51-114">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-115">Informations sur le fichier (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="6fb51-115">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-116">Noms d’entrée de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="6fb51-116">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-117">Informations sur les entrées de système de fichiers (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="6fb51-117">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6fb51-118">Noms de répertoires et de fichiers</span><span class="sxs-lookup"><span data-stu-id="6fb51-118">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="6fb51-119">Bien que vous puissiez énumérer immédiatement tous les fichiers dans les sous-répertoires d’un répertoire parent à l’aide de l’option <xref:System.IO.SearchOption.AllDirectories> de l’énumération <xref:System.IO.SearchOption> facultative, des erreurs <xref:System.UnauthorizedAccessException> peuvent rendre l’énumération incomplète.</span><span class="sxs-lookup"><span data-stu-id="6fb51-119">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="6fb51-120">Vous pouvez intercepter ces exceptions en énumérant d’abord les répertoires, puis les fichiers.</span><span class="sxs-lookup"><span data-stu-id="6fb51-120">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="6fb51-121">Exemples : utiliser la classe Directory</span><span class="sxs-lookup"><span data-stu-id="6fb51-121">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="6fb51-122">L’exemple suivant utilise la méthode <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> pour obtenir une liste des noms de répertoires de niveau supérieur dans un chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="6fb51-122">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="6fb51-123">L’exemple suivant utilise la méthode <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> pour énumérer de manière récursive tous les noms de fichiers dans un répertoire et dans les sous-répertoires qui correspondent à un certain modèle.</span><span class="sxs-lookup"><span data-stu-id="6fb51-123">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="6fb51-124">Il lit chaque ligne de chaque fichier et affiche les lignes qui contiennent la chaîne spécifiée, avec les noms de fichiers et chemins correspondants.</span><span class="sxs-lookup"><span data-stu-id="6fb51-124">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="6fb51-125">Exemples : utiliser la classe DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="6fb51-125">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="6fb51-126">L’exemple suivant utilise la méthode <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> pour lister une collection de répertoires de niveau supérieur dont <xref:System.IO.FileSystemInfo.CreationTimeUtc> est antérieur à une certaine valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="6fb51-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="6fb51-127">L’exemple suivant utilise la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> pour lister tous les fichiers dont <xref:System.IO.FileInfo.Length> dépasse 10 Mo.</span><span class="sxs-lookup"><span data-stu-id="6fb51-127">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="6fb51-128">Cet exemple énumère d’abord les répertoires de niveau supérieur, pour intercepter les éventuelles exceptions d’accès non autorisé, puis énumère les fichiers.</span><span class="sxs-lookup"><span data-stu-id="6fb51-128">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6fb51-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fb51-129">See also</span></span>

- [<span data-ttu-id="6fb51-130">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="6fb51-130">File and stream I/O</span></span>](index.md)
