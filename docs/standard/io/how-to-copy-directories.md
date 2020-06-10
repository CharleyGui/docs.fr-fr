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
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 65fe28c90a6cd6f0b3c8c32da19c1d9603900670
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662587"
---
# <a name="how-to-copy-directories"></a>Comment : copier des répertoires
Cette rubrique montre comment utiliser les classes d’E/S pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement.

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
- [E/S de fichier et de flux](index.md)
- [Tâches d’E/S courantes](common-i-o-tasks.md)
- [E/S sur fichier asynchrones](asynchronous-file-i-o.md)
