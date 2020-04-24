---
title: "Comment : écrire du texte dans des fichiers à l'aide de Streamwriter"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334495"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic

Cet exemple ouvre un objet <xref:System.IO.StreamWriter> avec la méthode `My.Computer.FileSystem.OpenTextFileWriter` et l’utilise pour écrire une chaîne dans un fichier texte avec la méthode <xref:System.IO.TextWriter.WriteLine%2A> de la classe <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).  
  
- Le disque est plein (<xref:System.IO.IOException>).  
  
- Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur. Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Guide pratique pour lire des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Écrire dans des fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
