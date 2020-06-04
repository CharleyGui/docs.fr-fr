---
title: 'Procédure : transformer la forme d’une arborescence XML'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 90fa23df09972eb76154dc47ce0a025e85a12ea3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397659"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Comment : transformer la forme d’une arborescence XML (Visual Basic)
La *forme* d’un document XML fait référence à ses noms d’éléments, à ses noms d’attributs et aux caractéristiques de sa hiérarchie.  
  
 Parfois, vous devrez modifier la forme d'un document XML. Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents. Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir. Pour plus d’informations sur la construction fonctionnelle, consultez [construction fonctionnelle (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).  
  
 Le premier exemple modifie l'organisation du document XML. Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.  
  
 Le deuxième exemple de cette rubrique crée un document XML avec une forme différente de celle du document source. Il modifie la casse des noms d’éléments, renomme certains éléments et laisse certains éléments de l’arborescence source en dehors de l’arborescence transformée.  
  
## <a name="example"></a>Exemple  
 Le code suivant modifie la forme d'un fichier XML à l'aide d'expressions de requête incorporées.  
  
 Le document XML source dans cet exemple contient un élément `Customers` sous l'élément `Root` qui contient tous les clients. Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes. Cet exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un élément `Orders` dans un élément `Customer`. Le document d'origine contient également un élément `CustomerID` dans l'élément `Order` ; cet élément sera supprimé du document reformé.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
<Customer CustomerID="GREAL">  
  <CompanyName>Great Lakes Food Market</CompanyName>  
  <ContactName>Howard Snyder</ContactName>  
  <ContactTitle>Marketing Manager</ContactTitle>  
  <Phone>(503) 555-7555</Phone>  
  <FullAddress>  
    <Address>2732 Baker Blvd.</Address>  
    <City>Eugene</City>  
    <Region>OR</Region>  
    <PostalCode>97403</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
...
</Root>
```  
  
## <a name="example"></a>Exemple  
 Cet exemple renomme certains éléments et convertit certains attributs en éléments.  
  
 Le code appelle `ConvertAddress`, qui renvoie une liste d'objets <xref:System.Xml.Linq.XElement>. L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Projections et transformations (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
