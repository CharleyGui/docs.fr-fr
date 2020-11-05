---
title: Objets XName et XNamespace atomisés-LINQ to XML
description: Découvrez comment les objets XName et XNamespace atomisés du même nom partagent une instance.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 05df7b5348fecebb7504ebb4e2623f688b6549e1
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400836"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a><span data-ttu-id="84cfc-103">Objets XName et XNamespace atomisés (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="84cfc-103">Atomized XName and XNamespace objects (LINQ to XML)</span></span>

<span data-ttu-id="84cfc-104">Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés*  ; autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="84cfc-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized* ; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="84cfc-105">Cela offre des avantages en matière de performances pour les requêtes : lorsque vous comparez deux noms atomisés pour l’égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet.</span><span class="sxs-lookup"><span data-stu-id="84cfc-105">This yields performance benefits for queries: when you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="84cfc-106">Le code sous-jacent n’a pas à effectuer de comparaisons de chaînes, ce qui prendra plus de temps.</span><span class="sxs-lookup"><span data-stu-id="84cfc-106">The underlying code doesn't have to do string comparisons, which would take longer.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="84cfc-107">Sémantique d’atomisation</span><span class="sxs-lookup"><span data-stu-id="84cfc-107">Atomization semantics</span></span>

<span data-ttu-id="84cfc-108">L’atomisation signifie que si deux <xref:System.Xml.Linq.XName> objets ont le même nom local et qu’ils se trouvent dans le même espace de noms, ils partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="84cfc-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they're in the same namespace, they share the same instance.</span></span> <span data-ttu-id="84cfc-109">De la même manière, si deux <xref:System.Xml.Linq.XNamespace> ont le même URI d'espace de noms, ils partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="84cfc-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="84cfc-110">Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public.</span><span class="sxs-lookup"><span data-stu-id="84cfc-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="84cfc-111">En effet, si le constructeur était public, vous pourriez créer un objet non atomisé.</span><span class="sxs-lookup"><span data-stu-id="84cfc-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="84cfc-112">Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en <xref:System.Xml.Linq.XName> ou en <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="84cfc-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="84cfc-113">Telle est la manière dont vous obtenez une instance de ces objets.</span><span class="sxs-lookup"><span data-stu-id="84cfc-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="84cfc-114">Vous ne pouvez pas obtenir une instance à l’aide d’un constructeur, car le constructeur est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="84cfc-114">You can't get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="84cfc-115"><xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d’égalité et d’inégalité, qui déterminent si les deux objets comparés sont des références à la même instance.</span><span class="sxs-lookup"><span data-stu-id="84cfc-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, which determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a><span data-ttu-id="84cfc-116">Exemple : créer des objets et afficher que les noms identiques partagent une instance</span><span class="sxs-lookup"><span data-stu-id="84cfc-116">Example: Create objects and show that identical names share an instance</span></span>

<span data-ttu-id="84cfc-117">Le code suivant crée certains objets <xref:System.Xml.Linq.XElement> et démontre que des noms identiques partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="84cfc-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```csharp
var r1 = new XElement("Root", "data1");
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

<span data-ttu-id="84cfc-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="84cfc-118">This example produces the following output:</span></span>

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="84cfc-119">Comme indiqué précédemment, l'avantage des objets atomisés est que lorsque vous utilisez l'une des méthodes d'axe qui accepte un <xref:System.Xml.Linq.XName> comme paramètre, la méthode d'axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.</span><span class="sxs-lookup"><span data-stu-id="84cfc-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="84cfc-120">L'exemple suivant passe un <xref:System.Xml.Linq.XName> à l'appel de méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, qui a ensuite une meilleure performance grâce au modèle d'atomisation.</span><span class="sxs-lookup"><span data-stu-id="84cfc-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```csharp
var root = new XElement("Root",
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

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1

For Each z In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="84cfc-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="84cfc-121">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```
