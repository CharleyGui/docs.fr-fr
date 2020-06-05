---
title: Objets XName et XNamespace atomisés (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 6a94bc0f2fd8013997e233b300fa19c12671bf29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383687"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Objets XName et XNamespace atomisés (LINQ to XML) (Visual Basic)

Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés* ; autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet. Ceci permet d'améliorer les performances des requêtes : lorsque vous comparez deux noms atomisés pour en vérifier l'égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet. Le code sous-jacent ne doit pas effectuer de comparaisons de chaînes, ce qui prendrait beaucoup de temps.

## <a name="atomization-semantics"></a>Sémantique d'atomisation

L'atomisation signifie que si deux objets <xref:System.Xml.Linq.XName> ont le même nom local et qu'ils soient dans le même espace de noms, ils partagent la même instance. De la même manière, si deux <xref:System.Xml.Linq.XNamespace> ont le même URI d'espace de noms, ils partagent la même instance.

Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public. En effet, si le constructeur était public, vous pourriez créer un objet non atomisé. Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en <xref:System.Xml.Linq.XName> ou en <xref:System.Xml.Linq.XNamespace>. Telle est la manière dont vous obtenez une instance de ces objets. Vous ne pouvez pas obtenir une instance à l'aide d'un constructeur, car le constructeur est inaccessible.

<xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d'égalité et d'inégalité pour déterminer si les deux objets comparés sont des références à la même instance.

## <a name="example"></a>Exemple

Le code suivant crée certains objets <xref:System.Xml.Linq.XElement> et démontre que des noms identiques partagent la même instance.

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

Cet exemple produit la sortie suivante :

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Comme indiqué précédemment, l'avantage des objets atomisés est que lorsque vous utilisez l'une des méthodes d'axe qui accepte un <xref:System.Xml.Linq.XName> comme paramètre, la méthode d'axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.

L'exemple suivant passe un <xref:System.Xml.Linq.XName> à l'appel de méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, qui a ensuite une meilleure performance grâce au modèle d'atomisation.

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

Cet exemple produit la sortie suivante :

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a>Voir aussi

- [Performances (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
