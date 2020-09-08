---
title: Comment contrôler le type d’une projection-LINQ to XML
description: Vous pouvez contrôler le type de collection que votre requête retourne ; Il n’est pas nécessaire qu’il s’agit d’un IEnumerable de XElements.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: c4be649a5f35f7e9cbe65332a60b1c8aeb2a66ea
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553532"
---
# <a name="how-to-control-the-type-of-a-projection-linq-to-xml"></a><span data-ttu-id="02c43-103">Comment contrôler le type d’une projection (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="02c43-103">How to control the type of a projection (LINQ to XML)</span></span>

<span data-ttu-id="02c43-104">La *projection* est le processus qui consiste à filtrer un jeu de données, à modifier sa forme et éventuellement son type.</span><span class="sxs-lookup"><span data-stu-id="02c43-104">*Projection* is the process of filtering a set of data, changing its shape and perhaps its type.</span></span> <span data-ttu-id="02c43-105">La plupart des expressions de requête effectuent des projections.</span><span class="sxs-lookup"><span data-stu-id="02c43-105">Most query expressions do projections.</span></span> <span data-ttu-id="02c43-106">La plupart des expressions de requête de cette section ont pour valeur <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , mais vous pouvez créer des collections d’autres types.</span><span class="sxs-lookup"><span data-stu-id="02c43-106">Most of the query expressions in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can create collections of other types.</span></span> <span data-ttu-id="02c43-107">Cet article explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="02c43-107">This article shows how to do this.</span></span>

## <a name="example-define-a-new-type-and-create-a-query-that-creates-an-ienumerable-of-that-type"></a><span data-ttu-id="02c43-108">Exemple : définir un nouveau type et créer une requête qui crée un IEnumerable de ce type</span><span class="sxs-lookup"><span data-stu-id="02c43-108">Example: Define a new type and create a query that creates an IEnumerable of that type</span></span>

<span data-ttu-id="02c43-109">L’exemple suivant définit un nouveau type, `Customer` , et l’expression de requête instancie `Customer` de nouveaux objets dans la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="02c43-109">The following example defines a new type, `Customer`, and the query expression instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="02c43-110">En conséquence, le type de l'expression de requête est <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.</span><span class="sxs-lookup"><span data-stu-id="02c43-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span> <span data-ttu-id="02c43-111">L’exemple utilise le document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md).</span><span class="sxs-lookup"><span data-stu-id="02c43-111">The example uses XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md).</span></span>

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

```vb
Public Class Customer
    Private customerIDValue As String
    Public Property CustomerID() As String
        Get
            Return customerIDValue
        End Get
        Set(ByVal value As String)
            customerIDValue = value
        End Set
    End Property

    Private companyNameValue As String
    Public Property CompanyName() As String
        Get
            Return companyNameValue
        End Get
        Set(ByVal value As String)
            companyNameValue = value
        End Set
    End Property

    Private contactNameValue As String
    Public Property ContactName() As String
        Get
            Return contactNameValue
        End Get
        Set(ByVal value As String)
            contactNameValue = value
        End Set
    End Property

    Public Sub New(ByVal customerID As String, _
                   ByVal companyName As String, _
                   ByVal contactName As String)
        CustomerIDValue = customerID
        CompanyNameValue = companyName
        ContactNameValue = contactName
    End Sub

    Public Overrides Function ToString() As String
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)
    End Function
End Class

Sub Main()
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
    Dim custList As IEnumerable(Of Customer) = _
        From el In custOrd.<Customers>.<Customer> _
        Select New Customer( _
            el.@<CustomerID>, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value _
        )
    For Each cust In custList
        Console.WriteLine(cust)
    Next
End Sub
```

<span data-ttu-id="02c43-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="02c43-112">This example produces the following output:</span></span>

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a><span data-ttu-id="02c43-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02c43-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="02c43-114">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c43-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
