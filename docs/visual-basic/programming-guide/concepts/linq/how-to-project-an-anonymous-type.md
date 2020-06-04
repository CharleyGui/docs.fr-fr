---
title: 'Procédure : projeter un type anonyme'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 459602eb7ede0bd055e00d3c7620cb95ec5408ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396478"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Comment : projeter un type anonyme (Visual Basic)
Dans certains cas, vous souhaiterez peut-être projeter une requête vers un nouveau type, bien que vous sachiez que vous n'utiliserez ce type que pendant une courte période. Il serait fastidieux de créer un nouveau type simplement pour l'utiliser dans la projection. Une approche plus efficace dans ce cas consiste à projeter vers un type anonyme. Les types anonymes vous permettent de définir une classe, puis de déclarer et d'initialiser un objet de cette classe sans donner de nom à la classe.  
  
 Les types anonymes sont l’implémentation C# du concept mathématique de *tuple*. Le terme mathématique tuple provenait à l’origine de la séquence simple, double, triple, quadruple, quintuple, n-tuple. Il fait référence à une séquence limitée d'objets, chacun d'un type spécifique. Parfois, on appelle cela une liste de paires nom/valeur. Par exemple, le contenu d’une adresse dans l’[Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) pourrait être exprimé de la façon suivante :  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Lorsque vous créez une instance d’un type anonyme, vous pouvez considérer que vous créez un tuple d’ordre n. Si vous écrivez une requête qui crée un tuple dans la clause `Select`, la requête retourne un `IEnumerable` du tuple.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la clause `Select` projette un type anonyme. L'exemple utilise ensuite `Dim` pour créer l'objet `IEnumerable`. Dans la boucle `For Each`, la variable d'itération devient une instance du type anonyme créé dans l'expression de la requête.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 Ce code génère la sortie suivante :  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Voir aussi

- [Projections et transformations (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
