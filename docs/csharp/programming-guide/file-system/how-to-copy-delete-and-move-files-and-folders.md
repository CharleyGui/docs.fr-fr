---
title: Comment copier, supprimer et déplacer des fichiers et des dossiers-Guide de programmation C#
description: Découvrez comment copier, supprimer et déplacer des fichiers et des dossiers à l’aide des classes file, Directory, FileInfo et DirectoryInfo.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 24595c9f5c75b70afb0ff079b6b93e35502f7fb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202511"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="74364-103">Comment copier, supprimer et déplacer des fichiers et des dossiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="74364-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>

<span data-ttu-id="74364-104">Les exemples suivants montrent comment copier, déplacer et supprimer des fichiers et dossiers de manière synchrone à l’aide des classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> et <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> à partir de l’espace de noms <xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74364-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="74364-105">Ces exemples ne fournissent pas de barre de progression ou autre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="74364-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="74364-106">Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez Guide pratique pour [fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="74364-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="74364-107">Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> pour fournir des événements qui vous permettent de calculer la progression quand vous travaillez sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="74364-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="74364-108">Une autre approche consiste à utiliser l’appel de code non managé pour appeler les méthodes pertinentes relatives aux fichiers dans le shell Windows.</span><span class="sxs-lookup"><span data-stu-id="74364-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="74364-109">Pour plus d’informations sur la façon d’effectuer ces opérations sur les fichiers de façon asynchrone, consultez [E/S de fichiers asynchrones](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="74364-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74364-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="74364-110">Example</span></span>  

 <span data-ttu-id="74364-111">L’exemple suivant montre comment copier des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="74364-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="74364-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="74364-112">Example</span></span>  

 <span data-ttu-id="74364-113">L’exemple suivant montre comment déplacer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="74364-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="74364-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="74364-114">Example</span></span>  

 <span data-ttu-id="74364-115">L’exemple suivant montre comment supprimer des fichiers et des répertoires.</span><span class="sxs-lookup"><span data-stu-id="74364-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="74364-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74364-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="74364-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="74364-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="74364-118">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="74364-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="74364-119">Comment fournir une boîte de dialogue de progression pour les opérations de fichier</span><span class="sxs-lookup"><span data-stu-id="74364-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="74364-120">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="74364-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="74364-121">Tâches d’e/s courantes</span><span class="sxs-lookup"><span data-stu-id="74364-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
