---
title: 'Comment : effectuer un ajout à des fichiers texte'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348872"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Guide pratique pour effectuer un ajout à des fichiers texte en Visual Basic

Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pour ajouter un fichier texte en spécifiant que le paramètre `append` est défini avec la valeur `True`.  
  
### <a name="to-append-to-a-text-file"></a>Pour effectuer un ajout à un fichier texte  
  
- Utilisez la méthode `WriteAllText`, en spécifiant le fichier cible et la chaîne à ajouter, et en affectant la valeur `True` au paramètre `append`.  
  
     Cet exemple écrit la chaîne `"This is a test string."` dans le fichier nommé `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
- Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).  
  
- Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).  
  
- Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
- Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).  
  
- L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Écriture dans des fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
