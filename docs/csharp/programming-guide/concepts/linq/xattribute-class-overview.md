---
title: Vue d’ensemble de la classe XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635663"
---
# <a name="xattribute-class-overview-c"></a>Vue d’ensemble de la classe XAttribute (C#)
Les attributs sont des paires nom/valeur associées à un élément. La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.  
  
## <a name="overview"></a>Vue d’ensemble  
 L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est semblable à l'utilisation des éléments. Leurs constructeurs sont similaires. Les méthodes que vous utilisez pour en récupérer des collections sont similaires. Une expression de requête LINQ pour une collection d’attributs ressemble beaucoup à une expression de requête LINQ pour une collection d’éléments.  
  
 L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé. Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.  
  
## <a name="the-xattribute-constructor"></a>Le constructeur XAttribute  
 Le constructeur suivant de la classe <xref:System.Xml.Linq.XAttribute> est celui que vous utiliserez le plus souvent :  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Crée un objet <xref:System.Xml.Linq.XAttribute>. L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Création d'un élément avec un attribut  
 Le code suivant illustre la tâche courante de création d’un élément qui contient un attribut :  
  
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
  
### <a name="functional-construction-of-attributes"></a>Construction fonctionnelle d'attributs  
 Vous pouvez construire des objets <xref:System.Xml.Linq.XAttribute> en ligne avec la construction d'objets <xref:System.Xml.Linq.XElement> de la manière suivante :  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>Les attributs ne sont pas des nœuds  
 Il existe certaines différences entre les attributs et les éléments. Les objets <xref:System.Xml.Linq.XAttribute> ne sont pas des nœuds dans l'arborescence XML. Il s'agit de paires nom/valeur associées à un élément XML. Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML. Bien que les objets <xref:System.Xml.Linq.XAttribute> ne soient pas réellement des nœuds de l'arborescence XML, l'utilisation d'objets <xref:System.Xml.Linq.XAttribute> s'apparente à l'utilisation d'objets <xref:System.Xml.Linq.XElement>.  
  
 Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud. De nombreux développeurs n'auront pas à se sourcier de cette distinction.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation LINQ to XML (C#)](./linq-to-xml-overview.md)
