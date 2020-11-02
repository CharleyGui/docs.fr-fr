---
title: 'Comment : copier des répertoires'
description: Découvrez comment copier des répertoires à l’aide de classes d’e/s qui copient de façon synchrone le contenu d’un répertoire vers un autre emplacement.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 476473d5c25ce29d070abbeef7fa29a7cb9621e1
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187981"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="13213-103">Comment : copier des répertoires</span><span class="sxs-lookup"><span data-stu-id="13213-103">How to: Copy directories</span></span>

<span data-ttu-id="13213-104">Cet article montre comment utiliser les classes d’e/s pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="13213-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="13213-105">Pour obtenir un exemple de copie de fichier asynchrone, consultez [E/S sur fichier asynchrones](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="13213-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="13213-106">Cet exemple copie des sous-répertoires en définissant la propriété `copySubDirs` de la méthode `DirectoryCopy` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="13213-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="13213-107">La méthode `DirectoryCopy` copie les sous-répertoires de manière récursive en s’appelant elle-même sur chaque sous-répertoire jusqu’à ce qu’il n’y ait plus rien à copier.</span><span class="sxs-lookup"><span data-stu-id="13213-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13213-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="13213-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="13213-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13213-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="13213-110">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="13213-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="13213-111">Tâches d’E/S courantes</span><span class="sxs-lookup"><span data-stu-id="13213-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="13213-112">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="13213-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
