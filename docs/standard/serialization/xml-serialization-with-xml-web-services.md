---
title: Sérialisation XML avec les services Web XML
description: En savoir plus sur la sérialisation XML en tant que mécanisme de transport utilisé dans l’architecture des services Web XML. La sérialisation XML est effectuée par la classe XmlSerializer.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML Web services, XML serialization
- XML serialization, XML Web services
- SOAP, XML serialization
- asmx files
- serialization, SOAP
- XML serialization, attributes
- attributes [.NET], XML serialization
- .asmx files
- encoded XML serialization
- literal XML serialization
- serialization, attributes
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
ms.openlocfilehash: 64b5911ca110ae4ef08f9003898bb817d8b8dd79
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676541"
---
# <a name="xml-serialization-with-xml-web-services"></a>Sérialisation XML avec les services Web XML

La sérialisation XML est le mécanisme de transport sous-jacent utilisé dans l'architecture de services Web XML, exécutée par la classe <xref:System.Xml.Serialization.XmlSerializer>. Pour contrôler le code XML généré par un service web XML, vous pouvez appliquer les attributs répertoriés dans [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md) aux classes, valeurs de retour, paramètres et champs d’un fichier utilisé pour créer un service web XML (.asmx). Pour plus d’informations sur la création d’un service Web XML, consultez [services Web XML à l’aide de ASP.net](/previous-versions/dotnet/netframework-4.0/ba0z6a33(v=vs.100)).  
  
## <a name="literal-and-encoded-styles"></a>Styles littéral et encodé  

 Le code XML généré par un service Web XML peut être mis en forme de deux manières : littéral ou encodé, comme expliqué dans personnalisation de la [mise en forme des messages SOAP](/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)). Par conséquent, il existe deux ensembles d'attributs qui contrôlent la sérialisation XML. Les attributs répertoriés dans [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md) sont conçus pour contrôler le code XML de style littéral. Les attributs répertoriés dans [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md) contrôlent le style de code encodé. En appliquant ces attributs de manière sélective, vous pouvez personnaliser une application afin qu'elle retourne l'un ou l'autre de ces styles, voire les deux. En outre, ces attributs peuvent être appliqués (le cas échéant) aux valeurs de retour et aux paramètres.  
  
### <a name="example-of-using-both-styles"></a>Exemple d'utilisation des deux styles  

 Lorsque vous créez un service Web XML, vous pouvez utiliser les deux ensembles d'attributs sur les méthodes. Dans l'exemple de code suivant, la classe intitulée `MyService` contient deux méthodes de services Web XML, `MyLiteralMethod` et `MyEncodedMethod`. Ces deux méthodes exécutent la même fonction : retourner une instance de la classe `Order`. Dans la classe `Order`, les attributs <xref:System.Xml.Serialization.XmlTypeAttribute> et <xref:System.Xml.Serialization.SoapTypeAttribute> s’appliquent tous deux au champ `OrderID`, mais leur propriété `ElementName` n’a pas la même valeur.  
  
 Pour exécuter l'exemple, collez le code dans un fichier portant une extension .asmx et placez ce fichier dans un répertoire virtuel géré par les Services Internet (IIS). Dans un navigateur HTML, tel qu'Internet Explorer, tapez le nom de l'ordinateur, du répertoire virtuel et du fichier.  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order {  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService {  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 L'exemple de code suivant appelle `MyLiteralMethod`. Le nom d'élément est remplacé par "LiteralOrderID."  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 L'exemple de code suivant appelle `MyEncodedMethod`. Le nom d'élément est "EncodedOrderID."  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-return-values"></a>Application d'attributs aux valeurs de retour  

 Vous pouvez également appliquer des attributs aux valeurs de retour pour contrôler l'espace de noms, le nom d'élément, etc. L'exemple de code suivant applique l'attribut `XmlElementAttribute` à la valeur de retour de la méthode `MyLiteralMethod`. Ainsi, vous pouvez contrôler l'espace de noms et le nom d'élément.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 Lorsqu'il est appelé, le code retourne du code XML qui se présente comme suit.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="attributes-applied-to-parameters"></a>Attributs appliqués à des paramètres  

 Vous pouvez également appliquer des attributs à des paramètres pour spécifier l'espace de noms, le nom d'élément, etc. L'exemple de code suivant ajoute un paramètre à la méthode `MyLiteralMethodResponse` et applique l'attribut `XmlAttributeAttribute` au paramètre. Le nom d'élément et l'espace de noms sont tous deux définis pour le paramètre.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}
```  
  
 La demande SOAP peut se présenter comme suit.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-classes"></a>Application d'attributs à des classes  

 Si vous devez contrôler l'espace de noms des éléments qui correspondent aux classes, vous pouvez appliquer `XmlTypeAttribute`, `XmlRootAttribute` et `SoapTypeAttribute`, si nécessaire. Les exemples de code suivants s'appliquent tous trois à la classe `Order`.  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order {  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Vous pouvez visualiser les résultats de l'application de `XmlTypeAttribute` et de `SoapTypeAttribute` lorsque vous examinez la description de service, comme illustré dans l'exemple de code suivant.  
  
```xml
<s:element name="BookOrderForm" type="s0:BigBookService" />
<s:complexType name="BigBookService">
  <s:sequence>
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />
  </s:sequence>

  <s:schema targetNamespace="http://tempuri.org/encodedTypes">
    <s:complexType name="SoapBookService">
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:schema>
</s:complexType>
```
  
 L'action de `XmlRootAttribute` est visible également dans les résultats des protocoles HTTP GET et HTTP POST, comme suit.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](how-to-override-encoded-soap-xml-serialization.md)
- [Introduction à la sérialisation XML](introducing-xml-serialization.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Comment : désérialiser un objet](how-to-deserialize-an-object.md)
