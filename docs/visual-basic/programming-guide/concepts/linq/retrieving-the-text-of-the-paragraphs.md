---
title: Récupération du texte des paragraphes
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 24167ade2d0326ef9382536f79f9e45eb22c89c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413386"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>Récupération du texte des paragraphes (Visual Basic)
Cet exemple s’appuie sur l’exemple précédent, [la récupération des paragraphes et de leurs styles (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md). Ce nouvel exemple récupère le texte de chaque paragraphe en tant que chaîne.  
  
 Pour récupérer le texte, cet exemple ajoute une requête supplémentaire qui itère au sein de la collection de types anonymes et projette une nouvelle collection d'un type anonyme avec l'ajout d'un nouveau membre, `Text`. Il utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.  
  
 Cette technique (qui consiste à projeter vers une collection d’un type anonyme, puis à utiliser cette collection pour projeter vers une nouvelle collection d’un type anonyme) est un idiome commun et utile. Cette requête pourrait avoir été écrite sans projeter vers le premier type anonyme. Toutefois, en raison de l'évaluation différée, procéder ainsi n'utilise pas beaucoup de puissance de traitement supplémentaire. L'idiome crée davantage d'objets à courte durée de vie sur la pile, mais cela ne nuit pas énormément aux performances.  
  
 Bien entendu, il serait possible d'écrire une requête unique contenant la fonctionnalité de récupération des paragraphes, du style de chaque paragraphe et du texte de chaque paragraphe. Toutefois, il est souvent utile de découper une requête compliquée en plusieurs requêtes car le code obtenu sera plus modulable et plus facile à maintenir. En outre, si vous avez besoin de réutiliser une partie de la requête, il est plus facile de refactoriser si les requêtes sont écrites de cette manière.  
  
 Ces requêtes, qui sont chaînées ensemble, utilisent le modèle de traitement examiné en détail dans la rubrique [Didacticiel : exécution différée (Visual Basic)](tutorial-deferred-execution.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et détermine le nœud d'élément, le nom de style et le texte de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.  
  
 Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 Cet exemple produit la sortie suivante lorsqu’elle est appliquée au document décrit dans [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>Étapes suivantes  
 L'exemple suivant montre comment utiliser une méthode d'extension, au lieu de <xref:System.Linq.Enumerable.Aggregate%2A>, pour concaténer plusieurs chaînes en une seule chaîne.  
  
- [Refactorisation à l’aide d’une méthode d’extension (Visual Basic)](refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Exécution et évaluation différées en LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
