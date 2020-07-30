---
title: Comment copier, supprimer et déplacer des fichiers et des dossiers-Guide de programmation C#
description: Découvrez comment copier, supprimer et déplacer des fichiers et des dossiers à l’aide des classes file, Directory, FileInfo et DirectoryInfo.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 208502651080f4fd614e34d1bf5b088dfb1207a6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303359"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Comment copier, supprimer et déplacer des fichiers et des dossiers (Guide de programmation C#)
Les exemples suivants montrent comment copier, déplacer et supprimer des fichiers et dossiers de manière synchrone à l’aide des classes <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType> et <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> à partir de l’espace de noms <xref:System.IO?displayProperty=nameWithType>. Ces exemples ne fournissent pas de barre de progression ou autre interface utilisateur. Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez Guide pratique pour [fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> pour fournir des événements qui vous permettent de calculer la progression quand vous travaillez sur plusieurs fichiers. Une autre approche consiste à utiliser l’appel de code non managé pour appeler les méthodes pertinentes relatives aux fichiers dans le shell Windows. Pour plus d’informations sur la façon d’effectuer ces opérations sur les fichiers de façon asynchrone, consultez [E/S de fichiers asynchrones](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment copier des fichiers et des répertoires.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déplacer des fichiers et des répertoires.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment supprimer des fichiers et des répertoires.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO?displayProperty=nameWithType>
- [Guide de programmation C#](../index.md)
- [Système de fichiers et Registre (Guide de programmation C#)](index.md)
- [Comment fournir une boîte de dialogue de progression pour les opérations de fichier](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [E/s de fichier et de flux](../../../standard/io/index.md)
- [Tâches d’e/s courantes](../../../standard/io/common-i-o-tasks.md)
