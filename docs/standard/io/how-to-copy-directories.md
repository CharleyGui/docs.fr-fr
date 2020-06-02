---
title: 'Comment : copier des répertoires'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: f71f428037f33fdbc692ca2f02a4c767998d684e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288574"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="91019-102">Comment : copier des répertoires</span><span class="sxs-lookup"><span data-stu-id="91019-102">How to: Copy directories</span></span>
<span data-ttu-id="91019-103">Cette rubrique montre comment utiliser les classes d’E/S pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="91019-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="91019-104">Pour obtenir un exemple de copie de fichier asynchrone, consultez [E/S sur fichier asynchrones](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="91019-104">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="91019-105">Cet exemple copie des sous-répertoires en définissant la propriété `copySubDirs` de la méthode `DirectoryCopy` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="91019-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="91019-106">La méthode `DirectoryCopy` copie les sous-répertoires de manière récursive en s’appelant elle-même sur chaque sous-répertoire jusqu’à ce qu’il n’y ait plus rien à copier.</span><span class="sxs-lookup"><span data-stu-id="91019-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91019-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="91019-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="91019-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91019-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="91019-109">E/S de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="91019-109">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="91019-110">Tâches d’E/S courantes</span><span class="sxs-lookup"><span data-stu-id="91019-110">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="91019-111">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="91019-111">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
