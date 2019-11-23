---
title: 'Comment : renommer un fichier'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334551"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Guide pratique pour renommer un fichier en Visual Basic

Utilisez la méthode `RenameFile` de l’objet `My.Computer.FileSystem` pour renommer un fichier en fournissant l’emplacement actuel, le nom actuel du fichier et le nouveau nom du fichier. Cette méthode ne peut pas être utilisée pour déplacer un fichier. Utilisez la méthode `MoveFile` pour déplacer et renommer le fichier.  
  
### <a name="to-rename-a-file"></a>Pour renommer un fichier  
  
- Pour renommer un fichier, utilisez la méthode `My.Computer.FileSystem.RenameFile`. Dans cet exemple, le nom de fichier `Test.txt` est remplacé par `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Système de fichiers - Traitement des lecteurs, dossiers et fichiers**. Pour plus d'informations, consultez [Code Snippets](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
- `newName` contient des informations de chemin (<xref:System.ArgumentException>).  
  
- Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
- `newName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).  
  
- Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
- Un fichier ou un répertoire porte déjà le nom spécifié dans `newName` (<xref:System.IO.IOException>).  
  
- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
- Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).  
  
- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).  
  
- L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Guide pratique : déplacer un fichier](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Création, suppression et déplacement de fichiers et de répertoires](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Guide pratique : créer une copie d'un fichier dans le même répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Guide pratique : créer une copie d'un fichier dans un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
