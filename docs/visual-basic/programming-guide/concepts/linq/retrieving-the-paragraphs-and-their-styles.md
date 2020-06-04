---
title: Récupération des paragraphes et de leurs styles
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413404"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Récupération des paragraphes et de leurs styles (Visual Basic)
Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe.  
  
 Cette requête est basée sur la requête de l’exemple précédent, [recherche du style de paragraphe par défaut (Visual Basic)](finding-the-default-paragraph-style.md), qui récupère le style par défaut à partir de la liste de styles. Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite. Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.  
  
 Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.  
  
## <a name="example"></a>Exemple  
 La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Cette expression est similaire à la source de la requête de l’exemple précédent, [recherche du style de paragraphe par défaut (Visual Basic)](finding-the-default-paragraph-style.md). La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>. La requête utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l'élément de corps, mais se trouvent deux niveaux au-dessous dans la hiérarchie. Grâce à l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera, que le document utilise des sections ou non.  
  
## <a name="example"></a>Exemple  
 La requête utilise une clause `Let` afin de déterminer l'élément qui contient le nœud de style. S'il n'y a aucun élément, `styleNode` a la valeur `Nothing` :  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 La clause `Let` utilise d'abord l'axe <xref:System.Xml.Linq.XContainer.Elements%2A> pour rechercher tous les éléments nommés `pPr`, puis utilise la méthode d'extension <xref:System.Xml.Linq.Extensions.Elements%2A> pour rechercher tous les éléments enfants nommés `pStyle`, et pour finir utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.FirstOrDefault%2A> pour convertir la collection en singleton. Si la collection est vide, `styleNode` a la valeur `Nothing`. Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`. Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `Nothing`, ce qui constitue le comportement souhaité de cette clause `Let`.  
  
 La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.  
  
 Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 Cet exemple produit la sortie suivante lorsqu’elle est appliquée au document décrit dans [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans la rubrique suivante, [extraction du texte des paragraphes (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.  
  
## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
