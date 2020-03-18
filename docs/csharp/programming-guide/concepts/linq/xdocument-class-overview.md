---
title: Vue d’ensemble de la classe XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590847"
---
# <a name="xdocument-class-overview-c"></a>Vue d’ensemble de la classe XDocument (C#)
Cette rubrique présente la classe <xref:System.Xml.Linq.XDocument>.  
  
## <a name="overview-of-the-xdocument-class"></a>Vue d'ensemble de la classe XDocument  
 La classe <xref:System.Xml.Linq.XDocument> contient les informations nécessaires pour un document XML valide. Cela inclut une déclaration XML, des instructions de traitement et des commentaires.  
  
 Notez que la création d'objets <xref:System.Xml.Linq.XDocument> est nécessaire uniquement si vous avez besoin de la fonctionnalité spécifique fournie par la classe <xref:System.Xml.Linq.XDocument>. Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>. L'utilisation directe de l'objet <xref:System.Xml.Linq.XElement> est un modèle de programmation plus simple.  
  
 <xref:System.Xml.Linq.XDocument> dérive de <xref:System.Xml.Linq.XContainer>. Par conséquent, il peut contenir des nœuds enfants. Toutefois, les objets <xref:System.Xml.Linq.XDocument> ne peuvent avoir qu'un seul nœud <xref:System.Xml.Linq.XElement> enfant. Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.  
  
## <a name="components-of-xdocument"></a>Composants de XDocument  
 Un objet <xref:System.Xml.Linq.XDocument> peut contenir les éléments suivants :  
  
- Un objet <xref:System.Xml.Linq.XDeclaration>. <xref:System.Xml.Linq.XDeclaration> vous permet de spécifier les parties pertinentes d'une déclaration XML : la version XML, l'encodage du document et si le document XML est autonome.  
  
- Un objet <xref:System.Xml.Linq.XElement>. Il s'agit du nœud racine du document XML.  
  
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XProcessingInstruction>. Une instruction de traitement communique des informations à une application qui traite le code XML.  
  
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XComment>. Les commentaires seront des frères de l'élément racine. L'objet <xref:System.Xml.Linq.XComment> ne peut pas être le premier argument de la liste, car un document XML valide ne peut pas commencer par un commentaire.  
  
- Un objet <xref:System.Xml.Linq.XDocumentType> pour le DTD.  
  
 Lorsque vous sérialisez un objet <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` a la valeur `null`, la sortie aura une déclaration XML à condition que la propriété `Writer.Settings.OmitXmlDeclaration` du writer ait la valeur `false` (valeur par défaut).  
  
 Par défaut, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] définit la version à « 1.0 » l'encodage à « utf-8 ».  
  
## <a name="using-xelement-without-xdocument"></a>Utilisation de XElement sans XDocument  
 Comme mentionné précédemment, la classe <xref:System.Xml.Linq.XElement> est la classe principale dans l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Dans de nombreux cas, votre application ne nécessitera pas la création d'un document. L'utilisation de la classe <xref:System.Xml.Linq.XElement> vous permet de créer une arborescence XML, de la modifier, de l'enregistrer et d'y ajouter d'autres arborescences XML.  
  
## <a name="using-xdocument"></a>Utilisation de XDocument  
 Pour construire un objet <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des objets <xref:System.Xml.Linq.XElement>.  
  
 Le code suivant crée un objet <xref:System.Xml.Linq.XDocument> et ses objets contenus associés.  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 Lorsque vous examinez le fichier test.xml, vous obtenez la sortie suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation LINQ to XML (C#)](./linq-to-xml-overview.md)
