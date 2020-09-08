---
title: Vue d’ensemble de la classe XDocument
description: La classe LINQ to XML XDocument contient les informations nécessaires pour un document XML valide. Dans de nombreux cas, vous n’avez pas besoin de la fonctionnalité d’un objet XDocument et pouvez utiliser un objet XElement à la place.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552388"
---
# <a name="xdocument-class-overview"></a>Vue d’ensemble de la classe XDocument

La <xref:System.Xml.Linq.XDocument> classe contient les informations nécessaires pour un document XML valide, qui inclut une déclaration XML, des instructions de traitement et des commentaires.

Vous devez uniquement créer des <xref:System.Xml.Linq.XDocument> objets si vous avez besoin de la fonctionnalité spécifique fournie par la <xref:System.Xml.Linq.XDocument> classe. Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>. L'utilisation directe de l'objet <xref:System.Xml.Linq.XElement> est un modèle de programmation plus simple.

<xref:System.Xml.Linq.XDocument> dérive de <xref:System.Xml.Linq.XContainer> , afin qu’il puisse contenir des nœuds enfants. Toutefois, les objets <xref:System.Xml.Linq.XDocument> ne peuvent avoir qu'un seul nœud <xref:System.Xml.Linq.XElement> enfant. Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.

## <a name="components-of-xdocument"></a>Composants de XDocument

Un objet <xref:System.Xml.Linq.XDocument> peut contenir les éléments suivants :

- Un objet <xref:System.Xml.Linq.XDeclaration>. <xref:System.Xml.Linq.XDeclaration> vous permet de spécifier les parties pertinentes d’une déclaration XML : la version XML, l’encodage du document et si le document XML est autonome.
- Un objet <xref:System.Xml.Linq.XElement>. Cet objet est le nœud racine du document XML.
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XProcessingInstruction>. Une instruction de traitement communique des informations à une application qui traite le code XML.
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XComment>. Les commentaires seront des frères de l'élément racine. L' <xref:System.Xml.Linq.XComment> objet ne peut pas être le premier argument de la liste, car il n’est pas valide pour qu’un document XML commence par un commentaire.
- Un objet <xref:System.Xml.Linq.XDocumentType> pour le DTD.

Lorsque vous sérialisez un objet <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` a la valeur `null`, la sortie aura une déclaration XML à condition que la propriété `Writer.Settings.OmitXmlDeclaration` du writer ait la valeur `false` (valeur par défaut).

Par défaut, LINQ to XML définit la version sur « 1,0 » et définit l’encodage sur « UTF-8 ».

## <a name="use-xelement-without-xdocument"></a>Utiliser XElement sans XDocument

Comme mentionné précédemment, la <xref:System.Xml.Linq.XElement> classe est la classe principale dans l’interface de programmation LINQ to XML. Dans de nombreux cas, votre application ne nécessite pas la création d’un document. À l’aide de la <xref:System.Xml.Linq.XElement> classe, vous pouvez :

- Créez une arborescence XML.
- Y ajouter d’autres arborescences XML.
- Modifiez l’arborescence XML.
- Enregistrez-le.

## <a name="use-xdocument"></a>Utiliser XDocument

Pour construire un objet <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des objets <xref:System.Xml.Linq.XElement>.

L’exemple suivant crée un <xref:System.Xml.Linq.XDocument> objet et ses objets contenus associés.

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

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
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
doc.Save("test.xml")
```

L’exemple génère cette sortie dans test.xml :

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

- [Présentation de LINQ to XML](linq-xml-overview.md)
