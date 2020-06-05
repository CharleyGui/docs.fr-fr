---
title: Analyse des fichiers texte avec l’objet TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 7b2cb0dd39d14dd94db661cc9cbacf99edf0e778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406675"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="fbb88-102">Analyse des fichiers texte avec l’objet TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbb88-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="fbb88-103">L’objet `TextFieldParser` permet d’analyser et de traiter de très gros fichiers structurés sous forme de colonnes de texte à largeur délimitée, tels que les fichiers journaux ou les informations de base de données héritée.</span><span class="sxs-lookup"><span data-stu-id="fbb88-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="fbb88-104">Analyser un fichier texte avec `TextFieldParser` revient à itérer un fichier texte, alors que la méthode d’analyse pour extraire des champs de texte est similaire aux méthodes de manipulation de chaînes utilisées pour segmenter des chaînes délimitées.</span><span class="sxs-lookup"><span data-stu-id="fbb88-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="fbb88-105">Analyse de fichiers texte de types différents</span><span class="sxs-lookup"><span data-stu-id="fbb88-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="fbb88-106">Les fichiers texte peuvent avoir des champs de largeur différente, délimités par un caractère tel qu’une virgule ou un espace de tabulation.</span><span class="sxs-lookup"><span data-stu-id="fbb88-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="fbb88-107">Définissez `TextFieldType` et le délimiteur, comme dans l’exemple suivant, qui utilise la méthode `SetDelimiters` pour définir un fichier texte délimité par des tabulations :</span><span class="sxs-lookup"><span data-stu-id="fbb88-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="fbb88-108">D’autres fichiers texte peuvent avoir des champs de largeur fixe.</span><span class="sxs-lookup"><span data-stu-id="fbb88-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="fbb88-109">Dans ce cas, vous devez définir `TextFieldType` sur `FixedWidth` et définir la largeur de chaque champ, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fbb88-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="fbb88-110">Cet exemple utilise la méthode `SetFieldWidths` pour définir les colonnes de texte : la première colonne a une largeur de 5 caractères, la deuxième de 10 et la troisième de 11 ; la quatrième colonne a une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="fbb88-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="fbb88-111">Une fois que vous avez défini le format, vous pouvez parcourir le fichier, à l’aide de la méthode `ReadFields`, pour traiter les lignes une par une.</span><span class="sxs-lookup"><span data-stu-id="fbb88-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="fbb88-112">Si un champ ne correspond pas au format spécifié, une exception <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> est levée.</span><span class="sxs-lookup"><span data-stu-id="fbb88-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="fbb88-113">Dans ce cas, les propriétés `ErrorLine` et `ErrorLineNumber` contiennent le texte à l’origine de l’exception et le numéro de ligne de ce texte.</span><span class="sxs-lookup"><span data-stu-id="fbb88-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="fbb88-114">Analyse de fichiers avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="fbb88-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="fbb88-115">La méthode `PeekChars` de l’objet `TextFieldParser` peut être utilisée pour vérifier chaque champ avant de le lire, ce qui vous permet de définir plusieurs formats de champs ainsi que le comportement approprié.</span><span class="sxs-lookup"><span data-stu-id="fbb88-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="fbb88-116">Pour plus d’informations, consultez [Guide pratique pour lire des fichiers texte avec plusieurs formats](how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="fbb88-116">For more information, see [How to: Read From Text Files with Multiple Formats](how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb88-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbb88-117">See also</span></span>

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
