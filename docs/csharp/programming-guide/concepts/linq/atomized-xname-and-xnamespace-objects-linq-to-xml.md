---
title: Objets XName et XNamespace atomisés (LINQ to XML) (C#)
description: En savoir plus sur les objets XName et XNamespace atomisés et la façon dont ils offrent des avantages en matière de performances pour les requêtes.
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104281"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Objets XName et XNamespace atomisés (LINQ to XML) (C#)
Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés* ; autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet. Ceci permet d'améliorer les performances des requêtes : lorsque vous comparez deux noms atomisés pour en vérifier l'égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet. Le code sous-jacent ne doit pas effectuer de comparaisons de chaînes, ce qui prendrait beaucoup de temps.  
  
## <a name="atomization-semantics"></a>Sémantique d'atomisation  
 L'atomisation signifie que si deux objets <xref:System.Xml.Linq.XName> ont le même nom local et qu'ils soient dans le même espace de noms, ils partagent la même instance. De la même manière, si deux <xref:System.Xml.Linq.XNamespace> ont le même URI d'espace de noms, ils partagent la même instance.  
  
 Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public. En effet, si le constructeur était public, vous pourriez créer un objet non atomisé. Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en <xref:System.Xml.Linq.XName> ou en <xref:System.Xml.Linq.XNamespace>. Telle est la manière dont vous obtenez une instance de ces objets. Vous ne pouvez pas obtenir une instance à l'aide d'un constructeur, car le constructeur est inaccessible.  
  
 <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d'égalité et d'inégalité pour déterminer si les deux objets comparés sont des références à la même instance.  
  
## <a name="example"></a>Exemple  
 Le code suivant crée certains objets <xref:System.Xml.Linq.XElement> et démontre que des noms identiques partagent la même instance.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Comme indiqué précédemment, l'avantage des objets atomisés est que lorsque vous utilisez l'une des méthodes d'axe qui accepte un <xref:System.Xml.Linq.XName> comme paramètre, la méthode d'axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.  
  
 L'exemple suivant passe un <xref:System.Xml.Linq.XName> à l'appel de méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, qui a ensuite une meilleure performance grâce au modèle d'atomisation.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
