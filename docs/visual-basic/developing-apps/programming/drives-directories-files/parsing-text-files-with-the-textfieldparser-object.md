---
title: Analyse des fichiers texte avec l’objet TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333844"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analyse des fichiers texte avec l’objet TextFieldParser (Visual Basic)

L’objet `TextFieldParser` permet d’analyser et de traiter de très gros fichiers structurés sous forme de colonnes de texte à largeur délimitée, tels que les fichiers journaux ou les informations de base de données héritée. Analyser un fichier texte avec `TextFieldParser` revient à itérer un fichier texte, alors que la méthode d’analyse pour extraire des champs de texte est similaire aux méthodes de manipulation de chaînes utilisées pour segmenter des chaînes délimitées.  
  
## <a name="parsing-different-types-of-text-files"></a>Analyse de fichiers texte de types différents  

 Les fichiers texte peuvent avoir des champs de largeur différente, délimités par un caractère tel qu’une virgule ou un espace de tabulation. Définissez `TextFieldType` et le délimiteur, comme dans l’exemple suivant, qui utilise la méthode `SetDelimiters` pour définir un fichier texte délimité par des tabulations :  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 D’autres fichiers texte peuvent avoir des champs de largeur fixe. Dans ce cas, vous devez définir `TextFieldType` sur `FixedWidth` et définir la largeur de chaque champ, comme dans l’exemple suivant. Cet exemple utilise la méthode `SetFieldWidths` pour définir les colonnes de texte : la première colonne a une largeur de 5 caractères, la deuxième de 10 et la troisième de 11 ; la quatrième colonne a une largeur variable.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Une fois que vous avez défini le format, vous pouvez parcourir le fichier, à l’aide de la méthode `ReadFields`, pour traiter les lignes une par une.  
  
 Si un champ ne correspond pas au format spécifié, une exception <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> est levée. Dans ce cas, les propriétés `ErrorLine` et `ErrorLineNumber` contiennent le texte à l’origine de l’exception et le numéro de ligne de ce texte.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analyse de fichiers avec plusieurs formats  

 La méthode `PeekChars` de l’objet `TextFieldParser` peut être utilisée pour vérifier chaque champ avant de le lire, ce qui vous permet de définir plusieurs formats de champs ainsi que le comportement approprié. Pour plus d’informations, consultez [Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
