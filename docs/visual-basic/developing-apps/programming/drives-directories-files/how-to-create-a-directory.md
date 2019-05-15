---
title: 'Procédure : créer un répertoire en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 54696dab41c99774bb3638e0c19837a906144d27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629078"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Procédure : créer un répertoire en Visual Basic
Utilisez la méthode `CreateDirectory` de l’objet `My.Computer.FileSystem` pour créer des répertoires.  
  
 Si le répertoire existe déjà, aucune exception n’est levée.  
  
### <a name="to-create-a-directory"></a>Pour créer un répertoire  
  
- Utilisez la méthode `CreateDirectory`, en spécifiant le chemin complet de l’emplacement où le répertoire doit être créé. Cet exemple crée le répertoire `NewDirectory` dans `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le format du nom du répertoire est incorrect. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).  
  
- Le répertoire parent du répertoire à créer est en lecture seule (<xref:System.IO.IOException>).  
  
- Le nom du répertoire est `Nothing` (<xref:System.ArgumentNullException>).  
  
- Le nom du répertoire est trop long (<xref:System.IO.PathTooLongException>).  
  
- Le nom du répertoire est un signe deux-points (:) (<xref:System.NotSupportedException>).  
  
- L’utilisateur n’a pas l’autorisation de créer le répertoire (<xref:System.UnauthorizedAccessException>).  
  
- L’utilisateur ne dispose pas des autorisations dans une situation de confiance partielle (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [Création, suppression et déplacement de fichiers et de répertoires](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
