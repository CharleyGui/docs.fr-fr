---
title: 'Comment : lire des fichiers texte de largeur fixe'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334624"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Guide pratique pour lire des fichiers texte de largeur fixe en Visual Basic

L’objet `TextFieldParser` permet d’analyser facilement et efficacement les fichiers texte structurés, tels que les journaux.  
  
 La propriété `TextFieldType` définit si le fichier analysé est un fichier délimité ou un fichier qui comporte des champs de texte de longueur fixe. Dans un fichier texte de largeur fixe, le champ situé à la fin peut avoir une largeur variable. Pour spécifier que le champ situé à la fin a une largeur variable, définissez-le pour que sa largeur soit inférieure ou égale à zéro.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Pour analyser un fichier texte de largeur fixe  
  
1. Créez un `TextFieldParser`. Le code suivant crée le `TextFieldParser` nommé `Reader` et ouvre le fichier `test.log`.  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Définissez la propriété `TextFieldType` en tant que `FixedWidth`, en définissant la largeur et le format. Le code suivant définit les colonnes de texte. La première a une largeur de 5 caractères, la deuxième de 10 caractères, la troisième de 11 caractères et la quatrième a une largeur variable.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Parcourez les champs du fichier à l’aide d’une boucle. Si des lignes sont endommagées, signalez une erreur et poursuivez l’analyse.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Fermez les blocs `While` et `Using` avec `End While` et `End Using`.  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Exemple  

 Cet exemple lit le fichier `test.log`.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- Une ligne ne peut pas être analysée à l’aide du format spécifié (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Le message d’exception spécifie la ligne qui provoque l’exception, tandis que la propriété <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> est assignée au texte contenu dans la ligne.  
  
- Le fichier spécifié n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
- Situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.Security.SecurityException>).  
  
- Le chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
- L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Comment : lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Comment : lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analyse des fichiers texte avec l'objet TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Dépannage : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
