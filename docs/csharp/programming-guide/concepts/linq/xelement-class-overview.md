---
title: Vue d’ensemble de la classe XElement (C#)
description: La classe XElement représente un élément XML en C#. Il s’agit de l’une des classes fondamentales de LINQ to XML. En savoir plus sur les fonctionnalités fournies par XElement.
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: f76f51703de054443f47531294777b43a9c0b004
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302176"
---
# <a name="xelement-class-overview-c"></a>Vue d’ensemble de la classe XElement (C#)
La classe <xref:System.Xml.Linq.XElement> est l'une des classes fondamentales dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Elle représente un élément XML. Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle. Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
Cette rubrique décrit la fonctionnalité fournie par la classe <xref:System.Xml.Linq.XElement>.  
  
## <a name="constructing-xml-trees"></a>Construction d'arborescences XML  
 Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :  
  
- Vous pouvez construire une arborescence XML dans du code. Pour plus d’informations, consultez [Création d’arborescences XML (C#)](./linq-to-xml-overview.md).  
  
- Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL). Pour plus d’informations, consultez [Analyse de code XML (C#)](./how-to-parse-a-string.md).  
  
- Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence. Pour plus d’informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Si vous avez un module qui peut écrire du contenu dans un objet <xref:System.Xml.XmlWriter>, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un writer, passer ce dernier au module, puis utiliser le contenu écrit dans l'objet <xref:System.Xml.XmlWriter> pour remplir l'arborescence XML.  
  
 Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Une autre technique très courante pour créer une arborescence XML consiste à utiliser les résultats d’une requête LINQ pour remplir une arborescence XML, comme illustré dans l’exemple suivant :  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
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
  
## <a name="serializing-xml-trees"></a>Sérialisation d'arborescences XML  
 Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.  
  
 Pour plus d’informations, consultez [Sérialisation d’arborescences XML (C#)](./preserving-white-space-while-serializing.md).  
  
## <a name="retrieving-xml-data-via-axis-methods"></a>Récupération de données XML par le biais de méthodes d'axe  
 Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres. Les requêtes LINQ opèrent sur les méthodes d’axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.  
  
 Pour plus d’informations, consultez [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md).  
  
## <a name="querying-xml-trees"></a>Interrogation d’arborescences XML  
 Vous pouvez écrire des requêtes LINQ qui extraient des données d’une arborescence XML.  
  
 Pour plus d’informations, consultez [Interrogation d’arborescences XML (C#)](./how-to-find-an-element-with-a-specific-attribute.md).  
  
## <a name="modifying-xml-trees"></a>Modification d’arborescences XML  
 Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs. Vous pouvez également supprimer un élément de son parent.  
  
 Pour plus d’informations, consultez [Modification d’arborescences XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation LINQ to XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
