---
title: 'How to: Join Two Collections (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 404a43f52fce141b515da389090c81c57186f2e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344532"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>How to: Join Two Collections (LINQ to XML) (Visual Basic)
Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut. Par exemple, l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) contient une liste de clients et une liste de commandes. Chaque élément `Customer` contient un attribut `CustomerID`. Chaque élément `Order` contient un élément `CustomerID`. L'élément `CustomerID` dans chaque commande fait référence à l'attribut `CustomerID` dans un client.  
  
 La rubrique [Exemple de fichier XSD : Clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contient un XSD qui peut servir à valider ce document. Il utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.  
  
 Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez tirer parti de cette relation en utilisant la clause `Join`.  
  
 Notez que dans la mesure où aucun index n'est disponible, une telle jointure présentera de faibles performances à l'exécution.  
  
 For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant joint les éléments `Customer` aux éléments `Order` et génère un nouveau document XML qui inclut l'élément `CompanyName` dans les commandes.  
  
 Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma dans [Exemple de fichier XSD : Clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Cela permet de s'assurer que la clause de jointure fonctionnera toujours.  
  
 Cette requête récupère d'abord tous les éléments `Customer`, puis les joint aux éléments `Order`. Elle sélectionne uniquement les commandes pour les clients dont le `CustomerID` est supérieur à « K ». Elle projette ensuite un nouvel élément `Order` qui contient les informations relatives aux clients dans chaque commande.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Notez que les performances d'une telle jointure ne seront pas très bonnes. Les jointures sont effectuées par le biais d'une recherche linéaire. Il n'y a aucun index ou table de hachage pour améliorer les performances.  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 Ce code génère la sortie suivante :  
  
```console
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Advanced Query Techniques (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
