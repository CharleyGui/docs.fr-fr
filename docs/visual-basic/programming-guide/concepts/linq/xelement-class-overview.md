---
title: Vue d’ensemble de la classe XElement
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413217"
---
# <a name="xelement-class-overview-visual-basic"></a>Vue d’ensemble de la classe XElement (Visual Basic)
La classe <xref:System.Xml.Linq.XElement> est l'une des classes fondamentales dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Elle représente un élément XML. Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle. Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>Fonctionnalité de XElement  
 Cette rubrique décrit la fonctionnalité fournie par la classe <xref:System.Xml.Linq.XElement>.  
  
### <a name="constructing-xml-trees"></a>Construction d'arborescences XML  
 Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :  
  
- Vous pouvez construire une arborescence XML dans du code. Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](creating-xml-trees.md).  
  
- Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL). Pour plus d’informations, consultez [analyse XML (Visual Basic)](parsing-xml.md).  
  
- Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence. Pour plus d’informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Si vous avez un module qui peut écrire du contenu dans un objet <xref:System.Xml.XmlWriter>, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un writer, passer ce dernier au module, puis utiliser le contenu écrit dans l'objet <xref:System.Xml.XmlWriter> pour remplir l'arborescence XML.  
  
 Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Une autre technique très courante pour créer une arborescence XML consiste à utiliser les résultats d’une requête LINQ pour remplir une arborescence XML, comme illustré dans l’exemple suivant :  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>Sérialisation d'arborescences XML  
 Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.  
  
 Pour plus d’informations, consultez [sérialisation d’arborescences XML (Visual Basic)](serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Récupération de données XML par le biais de méthodes d'axe  
 Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres. Les requêtes LINQ opèrent sur les méthodes d’axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.  
  
 Pour plus d’informations, consultez [LINQ to XML axes (Visual Basic)](linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Interrogation d’arborescences XML  
 Vous pouvez écrire des requêtes LINQ qui extraient des données d’une arborescence XML.  
  
 Pour plus d’informations, consultez [interrogation d’arborescences XML (Visual Basic)](querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modification d’arborescences XML  
 Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs. Vous pouvez également supprimer un élément de son parent.  
  
 Pour plus d’informations, consultez [modification d’arborescences XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
