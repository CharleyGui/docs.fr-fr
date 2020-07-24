---
title: Création d’arborescences XML en C# (LINQ to XML)
description: En savoir plus sur la création d’arborescences XML en C#, notamment la construction d’éléments et l’utilisation de constructeurs XElement.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3991f461c4c870a64320853ccd1d45026a8a6bf6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105479"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Création d’arborescences XML en C# (LINQ to XML)
Cette section fournit des informations sur la création d’arborescences XML en C#.  
  
 Pour plus d’informations sur l’utilisation des résultats de requêtes LINQ comme contenu d’un <xref:System.Xml.Linq.XElement>, consultez [Construction fonctionnelle (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Construction d’éléments
 Les signatures des constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> vous permettent de passer le contenu de l'élément ou attribut en tant qu'arguments du constructeur. Étant donné que l’un des constructeurs prend une quantité variable d’arguments, vous pouvez passer une quantité quelconque d’éléments enfants. Bien entendu, chacun de ces éléments enfants peut contenir ses propres éléments enfants. Pour tout élément, vous pouvez ajouter une quantité quelconque d'attributs.  
  
 Lors de l'ajout d'objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n'a pas de parent, les objets sont simplement attachés à l'arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML. Ceci est illustré dans le dernier exemple de cette rubrique.  
  
 Pour créer un objet `contacts`<xref:System.Xml.Linq.XElement>, vous pouvez utiliser le code suivant :  
  
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
  
 S'il est mis en retrait correctement, le code pour construire des objets <xref:System.Xml.Linq.XElement> ressemble étroitement à la structure du code XML sous-jacent.  
  
## <a name="xelement-constructors"></a>Constructeurs XElement  
 La classe <xref:System.Xml.Linq.XElement> utilise les constructeurs suivants pour la construction fonctionnelle. Notez qu'il existe d'autres constructeurs pour <xref:System.Xml.Linq.XElement>, mais ils ne sont pas répertoriés ici car ils ne sont pas utilisés pour la construction fonctionnelle.  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Crée un <xref:System.Xml.Linq.XElement>. Le paramètre `name` spécifie le nom de l'élément ; `content` spécifie le contenu de l'élément.|  
|`XElement(XName name)`|Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié.|  
|`XElement(XName name, params object[] content)`|Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié. Les attributs et/ou éléments enfants sont créés à partir du contenu de la liste de paramètres.|  
  
 Le paramètre `content` est extrêmement souple. Il prend en charge tout type d'objet qui est un enfant valide d'un objet <xref:System.Xml.Linq.XElement>. Les règles suivantes s'appliquent à différents types d'objets passés dans ce paramètre :  
  
- Une chaîne est ajoutée en tant que contenu de texte.  
  
- Un objet <xref:System.Xml.Linq.XElement> est ajouté en tant qu'élément enfant.  
  
- Un objet <xref:System.Xml.Linq.XAttribute> est ajouté en tant qu'attribut.  
  
- Un objet <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> est ajouté en tant que contenu enfant.  
  
- Un objet <xref:System.Collections.IEnumerable> est énuméré et ces règles sont appliquées de manière récursive aux résultats.  
  
- Pour tout autre type, sa méthode `ToString` est appelée et le résultat est ajouté en tant que contenu texte.  
  
### <a name="creating-an-xelement-with-content"></a>Création d’un XElement avec du contenu  
 Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple avec un appel de méthode unique. Pour cela, spécifiez le contenu comme second paramètre, comme suit :  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Vous pouvez passer tout type d'objet en tant que contenu. Par exemple, le code suivant crée un élément qui contient un nombre à virgule flottante en tant que contenu :  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 Le nombre à virgule flottante est boxed et passé au constructeur. Le nombre boxed est converti en une chaîne et utilisé comme contenu de l'élément.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Création d’un XElement avec un élément enfant  
 Si vous passez une instance de la classe <xref:System.Xml.Linq.XElement> comme argument de contenu, le constructeur crée un élément avec un élément enfant :  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Création d’un XElement avec plusieurs éléments enfants  
 Vous pouvez passer une quantité quelconque d'objets <xref:System.Xml.Linq.XElement> comme contenu. Chacun des objets <xref:System.Xml.Linq.XElement> est inclus en tant qu'élément enfant.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 En étendant l'exemple ci-dessus, vous pouvez créer une arborescence XML entière, comme suit :  
  
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
Console.WriteLine(contacts);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
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

### <a name="creating-an-xelement-with-an-xattribute"></a>Créer un XElement avec XAttribute
 Si vous passez une instance de la classe <xref:System.Xml.Linq.XAttribute> comme argument de contenu, le constructeur crée un élément avec un attribut :

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a>Création d’un élément vide  
 Pour créer un objet <xref:System.Xml.Linq.XElement> vide, vous ne passez aucun contenu au constructeur. L'exemple suivant crée un élément vide :  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Attachement et clonage  
 Comme mentionné précédemment, lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML.  

L’exemple suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément non apparenté à une arborescence.

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a>Voir aussi

- [Création d’arborescences XML (C#)](./linq-to-xml-overview.md)
