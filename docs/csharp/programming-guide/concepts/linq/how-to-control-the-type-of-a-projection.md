---
title: 'Procédure : Contrôler le type d’une projection (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: a44f7616beba3e07f6e44cc279c67468abc779e3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204093"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="afeae-102">Procédure : Contrôler le type d’une projection (C#)</span><span class="sxs-lookup"><span data-stu-id="afeae-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="afeae-103">La projection est un processus qui consiste à prendre un ensemble de données, à le filtrer, à modifier sa forme et même à modifier son type.</span><span class="sxs-lookup"><span data-stu-id="afeae-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="afeae-104">La plupart des expressions de requête effectuent des projections.</span><span class="sxs-lookup"><span data-stu-id="afeae-104">Most query expressions perform projections.</span></span> <span data-ttu-id="afeae-105">La plupart des expressions de requête illustrées dans cette section évaluent à l'objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, mais vous pouvez contrôler le type de projection afin de créer des collections d'autres types.</span><span class="sxs-lookup"><span data-stu-id="afeae-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="afeae-106">Cette rubrique montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="afeae-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afeae-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="afeae-107">Example</span></span>  
 <span data-ttu-id="afeae-108">L'exemple suivant définit un nouveau type, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="afeae-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="afeae-109">L'expression de requête instancie ensuite de nouveaux objets `Customer` dans la clause `Select`.</span><span class="sxs-lookup"><span data-stu-id="afeae-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="afeae-110">En conséquence, le type de l'expression de requête est <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.</span><span class="sxs-lookup"><span data-stu-id="afeae-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="afeae-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="afeae-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="afeae-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="afeae-112">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="afeae-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afeae-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
