---
title: Extraction de nœuds non triés par leur nom ou par l'index
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 55ea0e31bb8a2863dc0e0eb30f6ca5700c3110b8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155735"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Extraction de nœuds non triés par leur nom ou par l'index
**XmlNamedNodeMap**, appelé NamedNodeMap dans la spécification du World Wide Web Consortium (W3C), est requis pour gérer un ensemble non trié de nœuds tout en permettant de référencer les nœuds par leur nom ou sur base de l’index. Le seul moyen d’accéder à un **XmlNamedNodeMap** est le retour de **XmlNamedNodeMap** par une méthode ou une propriété. Trois méthodes ou propriétés retournent **XmlNamedNodeMap** :  
  
- XmlElement.Attributes ;  
  
- XmlDocumentType.Entities ;  
  
- XmlDocumentType.Notations.  
  
 Par exemple, la propriété **XmlDocumentType.Entities** obtient la collection de nœuds **XmlEntity** déclarée dans la déclaration du type de document. Cette collection est retournée sous la forme de **XmlNamedNodeMap**, et elle peut faire l’objet d’une itération à l’aide de la propriété **Count** pour afficher des informations d’entité. Pour obtenir un exemple d'itération sur **XmlNamedNodeMap**, consultez <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **XmlAttributeCollection** est dérivé de **XmlNamedNodeMap** et seuls les attributs sont modifiables, alors que les notations et entités sont en lecture seule. En utilisant **XmlNamedNodeMap** pour les attributs, vous pouvez obtenir des nœuds pour ces attributs en fonction de leurs noms XML. Il s'agit d'une méthode facile pour manipuler la collection d'attributs d'un nœud d'élément. À cela, nous pouvons opposer directement **XmlNodeList**, qui implémente également l’interface **IEnumerable**, avec toutefois un accesseur d’index plutôt qu’une chaîne. Les méthodes **RemoveNamedItem** et **SetNamedItem** sont uniquement utilisées sur **XmlAttributeCollection**. L’ajout ou la suppression d’un attribut dans une collection d’attributs, que ce soit au moyen **d’AttributeCollection** ou de l’implémentation **XmlNamedNodeMap**, modifie la collection d’attributs de l’élément. L'exemple de code suivant montre comment déplacer un attribut et créer un nouvel attribut.  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
    }  
}  
```  
  
 Pour examiner un exemple de code supplémentaire qui illustre la suppression d'un attribut **d’AttributeCollection**, consultez [Méthode XmlNamedNodeMap.RemoveNamedItem](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A). Pour plus d'informations sur les propriétés et méthodes, consultez [Membres XmlNamedNodeMap](xref:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
