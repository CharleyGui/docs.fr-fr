---
title: Comment projeter un type anonyme (C#)
description: Découvrez comment projeter une requête vers un type anonyme en C#. L’utilisation d’un type anonyme peut être plus simple que la création d’un nouveau type à utiliser brièvement.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104632"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Comment projeter un type anonyme (C#)
Dans certains cas, vous souhaiterez peut-être projeter une requête vers un nouveau type, bien que vous sachiez que vous n'utiliserez ce type que pendant une courte période. Il serait fastidieux de créer un nouveau type simplement pour l'utiliser dans la projection. Une approche plus efficace dans ce cas consiste à projeter vers un type anonyme. Les types anonymes vous permettent de définir une classe, puis de déclarer et d'initialiser un objet de cette classe sans donner de nom à la classe.  
  
 Les types anonymes sont l’implémentation C# du concept mathématique de *tuple*. Le terme mathématique tuple provenait à l’origine de la séquence simple, double, triple, quadruple, quintuple, n-tuple. Il fait référence à une séquence limitée d'objets, chacun d'un type spécifique. Parfois, on appelle cela une liste de paires nom/valeur. Par exemple, le contenu d’une adresse dans l’[Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) pourrait être exprimé de la façon suivante :  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Lorsque vous créez une instance d’un type anonyme, vous pouvez considérer que vous créez un tuple d’ordre n. Si vous écrivez une requête qui crée un tuple dans la clause `select`, la requête retourne un `IEnumerable` du tuple.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la clause `select` projette un type anonyme. L'exemple utilise ensuite `var` pour créer l'objet `IEnumerable`. Dans la boucle `foreach`, la variable d'itération devient une instance du type anonyme créé dans l'expression de la requête.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  