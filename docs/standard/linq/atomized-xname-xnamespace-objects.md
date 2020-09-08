---
title: Objets XName et XNamespace atomisés-LINQ to XML
description: Découvrez comment les objets XName et XNamespace atomisés du même nom partagent une instance.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc2be4d408385936598d94d34f9b452d950516d3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553543"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a>Objets XName et XNamespace atomisés (LINQ to XML)

Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés* ; autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet. Cela offre des avantages en matière de performances pour les requêtes : lorsque vous comparez deux noms atomisés pour l’égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet. Le code sous-jacent n’a pas à effectuer de comparaisons de chaînes, ce qui prendra plus de temps.

## <a name="atomization-semantics"></a>Sémantique d’atomisation

L’atomisation signifie que si deux <xref:System.Xml.Linq.XName> objets ont le même nom local et qu’ils se trouvent dans le même espace de noms, ils partagent la même instance. De la même manière, si deux <xref:System.Xml.Linq.XNamespace> ont le même URI d'espace de noms, ils partagent la même instance.

Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public. En effet, si le constructeur était public, vous pourriez créer un objet non atomisé. Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en <xref:System.Xml.Linq.XName> ou en <xref:System.Xml.Linq.XNamespace>. Telle est la manière dont vous obtenez une instance de ces objets. Vous ne pouvez pas obtenir une instance à l’aide d’un constructeur, car le constructeur est inaccessible.

<xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d’égalité et d’inégalité, qui déterminent si les deux objets comparés sont des références à la même instance.

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a>Exemple : créer des objets et afficher que les noms identiques partagent une instance

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
