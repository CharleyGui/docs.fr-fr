---
title: 'Comment : copier des répertoires'
description: Découvrez comment copier des répertoires à l’aide de classes d’e/s qui copient de façon synchrone le contenu d’un répertoire vers un autre emplacement.
ms.date: 12/27/2018
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
ms.openlocfilehash: b81723b9ed7067826692e8383bf64058d4295f0c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830829"
---
# <a name="how-to-copy-directories"></a>Comment : copier des répertoires

Cet article montre comment utiliser les classes d’e/s pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement.

Pour obtenir un exemple de copie de fichier asynchrone, consultez [E/S sur fichier asynchrones](asynchronous-file-i-o.md).

Cet exemple copie des sous-répertoires en définissant la propriété `copySubDirs` de la méthode `DirectoryCopy` sur `true`. La méthode `DirectoryCopy` copie les sous-répertoires de manière récursive en s’appelant elle-même sur chaque sous-répertoire jusqu’à ce qu’il n’y ait plus rien à copier.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [E/s de fichier et de flux](index.md)
- [Tâches d’E/S courantes](common-i-o-tasks.md)
- [E/S sur fichier asynchrones](asynchronous-file-i-o.md)
