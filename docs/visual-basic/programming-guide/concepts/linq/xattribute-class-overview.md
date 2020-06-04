---
title: Vue d'ensemble de la classe XAttribute
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413204"
---
# <a name="xattribute-class-overview-visual-basic"></a>Vue d’ensemble de la classe XAttribute (Visual Basic)
Les attributs sont des paires nom/valeur associées à un élément. La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.  
  
## <a name="overview"></a>Vue d’ensemble  
 L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est semblable à l'utilisation des éléments. Leurs constructeurs sont similaires. Les méthodes que vous utilisez pour en récupérer des collections sont similaires. Une expression de requête LINQ pour une collection d’attributs a une apparence très semblable à une expression de requête LINQ pour une collection d’éléments.  
  
 L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé. Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.  
  
## <a name="the-xattribute-constructor"></a>Le constructeur XAttribute  
 Le constructeur suivant de la classe <xref:System.Xml.Linq.XAttribute> est celui que vous utiliserez le plus souvent :  
  
|Constructeur|Description|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Crée un objet <xref:System.Xml.Linq.XAttribute>. L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Création d'un élément avec un attribut  
 Le code suivant illustre un élément qui contient un attribut à l’aide de littéraux XML dans Visual Basic :  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Construction fonctionnelle d'attributs  
 Vous pouvez construire des objets <xref:System.Xml.Linq.XAttribute> en ligne avec la construction d'objets <xref:System.Xml.Linq.XElement> de la manière suivante :  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
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

- [Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
