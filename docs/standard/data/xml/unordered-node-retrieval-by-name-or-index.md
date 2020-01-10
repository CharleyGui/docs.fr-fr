---
title: Extraction de nœuds non triés par leur nom ou par l'index
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 8c6819b4c1628d9e09a9bbf96ae8d5edbb6c643d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710074"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="0517c-102">Extraction de nœuds non triés par leur nom ou par l'index</span><span class="sxs-lookup"><span data-stu-id="0517c-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="0517c-103">**XmlNamedNodeMap**, appelé NamedNodeMap dans la spécification du World Wide Web Consortium (W3C), est requis pour gérer un ensemble non trié de nœuds tout en permettant de référencer les nœuds par leur nom ou sur base de l’index.</span><span class="sxs-lookup"><span data-stu-id="0517c-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="0517c-104">Le seul moyen d’accéder à un **XmlNamedNodeMap** est le retour de **XmlNamedNodeMap** par une méthode ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="0517c-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="0517c-105">Trois méthodes ou propriétés retournent **XmlNamedNodeMap** :</span><span class="sxs-lookup"><span data-stu-id="0517c-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="0517c-106">XmlElement.Attributes ;</span><span class="sxs-lookup"><span data-stu-id="0517c-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="0517c-107">XmlDocumentType.Entities ;</span><span class="sxs-lookup"><span data-stu-id="0517c-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="0517c-108">XmlDocumentType.Notations.</span><span class="sxs-lookup"><span data-stu-id="0517c-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="0517c-109">Par exemple, la propriété **XmlDocumentType.Entities** obtient la collection de nœuds **XmlEntity** déclarée dans la déclaration du type de document.</span><span class="sxs-lookup"><span data-stu-id="0517c-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="0517c-110">Cette collection est retournée sous la forme de **XmlNamedNodeMap**, et elle peut faire l’objet d’une itération à l’aide de la propriété **Count** pour afficher des informations d’entité.</span><span class="sxs-lookup"><span data-stu-id="0517c-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="0517c-111">Pour obtenir un exemple d'itération sur **XmlNamedNodeMap**, consultez <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="0517c-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="0517c-112">**XmlAttributeCollection** est dérivé de **XmlNamedNodeMap** et seuls les attributs sont modifiables, alors que les notations et entités sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="0517c-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="0517c-113">En utilisant **XmlNamedNodeMap** pour les attributs, vous pouvez obtenir des nœuds pour ces attributs en fonction de leurs noms XML.</span><span class="sxs-lookup"><span data-stu-id="0517c-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="0517c-114">Il s'agit d'une méthode facile pour manipuler la collection d'attributs d'un nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="0517c-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="0517c-115">À cela, nous pouvons opposer directement **XmlNodeList**, qui implémente également l’interface **IEnumerable**, avec toutefois un accesseur d’index plutôt qu’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="0517c-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="0517c-116">Les méthodes **RemoveNamedItem** et **SetNamedItem** sont uniquement utilisées sur **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="0517c-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="0517c-117">L’ajout ou la suppression d’un attribut dans une collection d’attributs, que ce soit au moyen **d’AttributeCollection** ou de l’implémentation **XmlNamedNodeMap**, modifie la collection d’attributs de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0517c-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="0517c-118">L'exemple de code suivant montre comment déplacer un attribut et créer un nouvel attribut.</span><span class="sxs-lookup"><span data-stu-id="0517c-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="0517c-119">Pour examiner un exemple de code supplémentaire qui illustre la suppression d'un attribut **d’AttributeCollection**, consultez [Méthode XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span><span class="sxs-lookup"><span data-stu-id="0517c-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="0517c-120">Pour plus d'informations sur les propriétés et méthodes, consultez [Membres XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="0517c-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0517c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0517c-121">See also</span></span>

- [<span data-ttu-id="0517c-122">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="0517c-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
