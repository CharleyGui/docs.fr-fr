---
title: Comment projeter un type anonyme (C)
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345731"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="91d6f-102">Comment projeter un type anonyme (C)</span><span class="sxs-lookup"><span data-stu-id="91d6f-102">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="91d6f-103">Dans certains cas, vous souhaiterez peut-être projeter une requête vers un nouveau type, bien que vous sachiez que vous n'utiliserez ce type que pendant une courte période.</span><span class="sxs-lookup"><span data-stu-id="91d6f-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="91d6f-104">Il serait fastidieux de créer un nouveau type simplement pour l'utiliser dans la projection.</span><span class="sxs-lookup"><span data-stu-id="91d6f-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="91d6f-105">Une approche plus efficace dans ce cas consiste à projeter vers un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="91d6f-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="91d6f-106">Les types anonymes vous permettent de définir une classe, puis de déclarer et d'initialiser un objet de cette classe sans donner de nom à la classe.</span><span class="sxs-lookup"><span data-stu-id="91d6f-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="91d6f-107">Les types anonymes sont l’implémentation C# du concept mathématique de *tuple*.</span><span class="sxs-lookup"><span data-stu-id="91d6f-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="91d6f-108">Le terme mathématique tuple provenait à l’origine de la séquence simple, double, triple, quadruple, quintuple, n-tuple.</span><span class="sxs-lookup"><span data-stu-id="91d6f-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="91d6f-109">Il fait référence à une séquence limitée d'objets, chacun d'un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="91d6f-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="91d6f-110">Parfois, on appelle cela une liste de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="91d6f-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="91d6f-111">Par exemple, le contenu d’une adresse dans l’[Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) pourrait être exprimé de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="91d6f-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="91d6f-112">Lorsque vous créez une instance d’un type anonyme, vous pouvez considérer que vous créez un tuple d’ordre n.</span><span class="sxs-lookup"><span data-stu-id="91d6f-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="91d6f-113">Si vous écrivez une requête qui crée un tuple dans la clause `select`, la requête retourne un `IEnumerable` du tuple.</span><span class="sxs-lookup"><span data-stu-id="91d6f-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d6f-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="91d6f-114">Example</span></span>  
 <span data-ttu-id="91d6f-115">Dans cet exemple, la clause `select` projette un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="91d6f-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="91d6f-116">L'exemple utilise ensuite `var` pour créer l'objet `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="91d6f-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="91d6f-117">Dans la boucle `foreach`, la variable d'itération devient une instance du type anonyme créé dans l'expression de la requête.</span><span class="sxs-lookup"><span data-stu-id="91d6f-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="91d6f-118">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="91d6f-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="91d6f-119">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="91d6f-119">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  