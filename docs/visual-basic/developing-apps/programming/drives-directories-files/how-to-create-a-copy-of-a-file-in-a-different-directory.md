---
title: 'Procédure : créer une copie d’un fichier dans un autre répertoire'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 3b4b41e105d6bb6a17fbb688aa4718b33c23b9d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401691"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Guide pratique pour créer une copie d'un fichier dans un autre répertoire en Visual Basic

La méthode `My.Computer.FileSystem.CopyFile` permet de copier des fichiers. Ses paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d’afficher la progression de l’opération et d’autoriser l’utilisateur à annuler l’opération.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Pour copier un fichier texte dans un autre dossier  
  
- Utilisez la méthode `CopyFile` pour copier un fichier, en spécifiant un fichier source et le répertoire cible. Le paramètre `overwrite` permet de spécifier s’il faut remplacer les fichiers existants. Les exemples de code suivants illustrent comment utiliser `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception :  
  
- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
- Le système n’a pas pu récupérer le chemin absolu (<xref:System.ArgumentException>).  
  
- Le chemin n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
- Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
- Le chemin combiné pointe vers un répertoire existant (<xref:System.IO.IOException>).  
  
- Le fichier de destination existe et `overwrite` a la valeur `False` (<xref:System.IO.IOException>).  
  
- L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).  
  
- Un fichier du même nom dans le dossier cible est en cours d’utilisation (<xref:System.IO.IOException>).  
  
- Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).  
  
- `ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l’utilisateur a annulé l’opération (<xref:System.OperationCanceledException>).  
  
- `ShowUI`a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur d’E/S non spécifiée se produit (<xref:System.OperationCanceledException>).  
  
- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
- L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).  
  
- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Procédure : copier des fichiers avec un modèle spécifique dans un répertoire](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Procédure : créer une copie d’un fichier dans le même répertoire](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Procédure : copier un répertoire vers un autre répertoire](how-to-copy-a-directory-to-another-directory.md)
- [Procédure : renommer un fichier](how-to-rename-a-file.md)
