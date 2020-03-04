---
title: "Comment : spécifier un nom d'élément différent pour un flux XML"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 6aaff20e2955fc9f121b3e60b14c0bbcf7515660
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159856"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="052e6-102">Comment : spécifier un nom d'élément différent pour un flux XML</span><span class="sxs-lookup"><span data-stu-id="052e6-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
  
<span data-ttu-id="052e6-103">Via <xref:System.Xml.Serialization.XmlSerializer>, vous pouvez générer plusieurs flux de données XML avec un même ensemble de classes.</span><span class="sxs-lookup"><span data-stu-id="052e6-103">Using the <xref:System.Xml.Serialization.XmlSerializer>, you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="052e6-104">Vous pouvez procéder ainsi car deux services Web XML différents nécessitent les mêmes informations de base, avec seulement de légères différences.</span><span class="sxs-lookup"><span data-stu-id="052e6-104">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="052e6-105">Par exemple, imaginez deux services Web XML qui traitent des commandes de livres. Ils nécessitent donc tous les deux des numéros ISBN.</span><span class="sxs-lookup"><span data-stu-id="052e6-105">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="052e6-106">Un service utilise la balise \<ISBN> tandis que l’autre utilise la balise \<BookID>.</span><span class="sxs-lookup"><span data-stu-id="052e6-106">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="052e6-107">Vous disposez d'une classe nommée `Book` qui contient un champ nommé `ISBN`.</span><span class="sxs-lookup"><span data-stu-id="052e6-107">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="052e6-108">Lorsqu'une instance de la classe `Book` est sérialisée, elle utilise par défaut le nom de membre (ISBN) comme nom d'élément de balise.</span><span class="sxs-lookup"><span data-stu-id="052e6-108">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="052e6-109">Pour le premier service Web XML, c'est ce qui est prévu.</span><span class="sxs-lookup"><span data-stu-id="052e6-109">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="052e6-110">Toutefois, pour envoyer le flux de données XML au deuxième service Web XML, vous devez substituer la sérialisation afin que le nom d'élément de la balise soit `BookID`.</span><span class="sxs-lookup"><span data-stu-id="052e6-110">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="052e6-111">Pour créer un flux de données XML avec un nom d'élément différent</span><span class="sxs-lookup"><span data-stu-id="052e6-111">To create an XML stream with an alternate element name</span></span>  
  
1. <span data-ttu-id="052e6-112">Créez une instance de la classe <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="052e6-112">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2. <span data-ttu-id="052e6-113">Affectez "BookID" à <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> de <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="052e6-113">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3. <span data-ttu-id="052e6-114">Créez une instance de la classe <xref:System.Xml.Serialization.XmlAttributes>.</span><span class="sxs-lookup"><span data-stu-id="052e6-114">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4. <span data-ttu-id="052e6-115">Ajoutez l'objet `XmlElementAttribute` à la collection accessible via la propriété <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> de <xref:System.Xml.Serialization.XmlAttributes>.</span><span class="sxs-lookup"><span data-stu-id="052e6-115">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5. <span data-ttu-id="052e6-116">Créez une instance de la classe <xref:System.Xml.Serialization.XmlAttributeOverrides>.</span><span class="sxs-lookup"><span data-stu-id="052e6-116">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6. <span data-ttu-id="052e6-117">Ajoutez `XmlAttributes` à <xref:System.Xml.Serialization.XmlAttributeOverrides>, en passant le type de l'objet à substituer et le nom du membre substitué.</span><span class="sxs-lookup"><span data-stu-id="052e6-117">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7. <span data-ttu-id="052e6-118">Créez une instance de la classe `XmlSerializer` avec `XmlAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="052e6-118">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8. <span data-ttu-id="052e6-119">Créez une instance de la classe `Book` et sérialisez ou désérialisez-la.</span><span class="sxs-lookup"><span data-stu-id="052e6-119">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="052e6-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="052e6-120">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="052e6-121">Le flux de données XML peut se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="052e6-121">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="052e6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="052e6-122">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>
- <xref:System.Xml.Serialization.XmlAttributes>
- <xref:System.Xml.Serialization.XmlAttributeOverrides>
- [<span data-ttu-id="052e6-123">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="052e6-123">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="052e6-124">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="052e6-124">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="052e6-125">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="052e6-125">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
