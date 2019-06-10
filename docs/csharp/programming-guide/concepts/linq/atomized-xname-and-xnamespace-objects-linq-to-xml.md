---
title: Objets XName et XNamespace atomisés (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 0d21397e6885b892f6ac1904e38bd85a78ae07ab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487599"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="3e29d-102">Objets XName et XNamespace atomisés (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e29d-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3e29d-103">Les objets <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> sont *atomisés* ; autrement dit, s’ils contiennent le même nom qualifié, ils font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="3e29d-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="3e29d-104">Ceci permet d’améliorer les performances des requêtes : quand vous comparez deux noms atomisés pour en vérifier l’égalité, le langage intermédiaire sous-jacent doit seulement déterminer si les deux références pointent vers le même objet.</span><span class="sxs-lookup"><span data-stu-id="3e29d-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="3e29d-105">Le code sous-jacent ne doit pas effectuer de comparaisons de chaînes, ce qui prendrait beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="3e29d-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="3e29d-106">Sémantique d'atomisation</span><span class="sxs-lookup"><span data-stu-id="3e29d-106">Atomization Semantics</span></span>  
 <span data-ttu-id="3e29d-107">L'atomisation signifie que si deux objets <xref:System.Xml.Linq.XName> ont le même nom local et qu'ils soient dans le même espace de noms, ils partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="3e29d-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="3e29d-108">De la même manière, si deux <xref:System.Xml.Linq.XNamespace> ont le même URI d'espace de noms, ils partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="3e29d-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="3e29d-109">Pour qu'une classe autorise les objets atomisés, le constructeur de cette classe doit être privé, et non public.</span><span class="sxs-lookup"><span data-stu-id="3e29d-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="3e29d-110">En effet, si le constructeur était public, vous pourriez créer un objet non atomisé.</span><span class="sxs-lookup"><span data-stu-id="3e29d-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="3e29d-111">Les classes <xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent un opérateur de conversion implicite pour convertir une chaîne en <xref:System.Xml.Linq.XName> ou en <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="3e29d-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="3e29d-112">Telle est la manière dont vous obtenez une instance de ces objets.</span><span class="sxs-lookup"><span data-stu-id="3e29d-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="3e29d-113">Vous ne pouvez pas obtenir une instance à l'aide d'un constructeur, car le constructeur est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="3e29d-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="3e29d-114"><xref:System.Xml.Linq.XName> et <xref:System.Xml.Linq.XNamespace> implémentent également les opérateurs d'égalité et d'inégalité pour déterminer si les deux objets comparés sont des références à la même instance.</span><span class="sxs-lookup"><span data-stu-id="3e29d-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e29d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e29d-115">Example</span></span>  
 <span data-ttu-id="3e29d-116">Le code suivant crée certains objets <xref:System.Xml.Linq.XElement> et démontre que des noms identiques partagent la même instance.</span><span class="sxs-lookup"><span data-stu-id="3e29d-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="3e29d-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3e29d-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="3e29d-118">Comme indiqué précédemment, l'avantage des objets atomisés est que lorsque vous utilisez l'une des méthodes d'axe qui accepte un <xref:System.Xml.Linq.XName> comme paramètre, la méthode d'axe doit seulement déterminer que deux noms font référence à la même instance pour sélectionner les éléments voulus.</span><span class="sxs-lookup"><span data-stu-id="3e29d-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="3e29d-119">L'exemple suivant passe un <xref:System.Xml.Linq.XName> à l'appel de méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, qui a ensuite une meilleure performance grâce au modèle d'atomisation.</span><span class="sxs-lookup"><span data-stu-id="3e29d-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="3e29d-120">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3e29d-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
