---
title: Qualifier des noms d’attributs et d’éléments XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 383dc7687e67e183b86598857067801c950b0312
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545090"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="2faba-102">Qualifier des noms d’attributs et d’éléments XML</span><span class="sxs-lookup"><span data-stu-id="2faba-102">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="2faba-103">Les espaces de noms XML contenus par les instances de la classe <xref:System.Xml.Serialization.XmlSerializerNamespaces> doivent se conformer à la spécification World Wide Web Consortium (W3C) appelée [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="2faba-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="2faba-104">Les espaces de noms XML offrent une méthode permettant de qualifier les noms d'éléments et d'attributs XML dans des documents XML.</span><span class="sxs-lookup"><span data-stu-id="2faba-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="2faba-105">Un nom qualifié se compose d'un préfixe et d'un nom local, séparés par le caractère deux-points.</span><span class="sxs-lookup"><span data-stu-id="2faba-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="2faba-106">Le préfixe joue uniquement le rôle d'espace réservé ; il est mappé à un URI (Universal Resource Identifier) qui spécifie un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2faba-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="2faba-107">L'association entre l'espace de noms URI géré de manière universelle et le nom local génère un nom dont l'unicité universelle est garantie.</span><span class="sxs-lookup"><span data-stu-id="2faba-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="2faba-108">En créant une instance de `XmlSerializerNamespaces` et en ajoutant les paires d'espaces de noms à l'objet, vous pouvez spécifier les préfixes utilisés dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="2faba-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="2faba-109">Pour créer des noms qualifiés dans un document XML</span><span class="sxs-lookup"><span data-stu-id="2faba-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="2faba-110">Créez une instance de la classe `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="2faba-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="2faba-111">Ajoutez tous les préfixes et paires d'espaces de noms à `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="2faba-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="2faba-112">Appliquez l'attribut `System.Xml.Serialization` approprié à chaque membre ou classe que <xref:System.Xml.Serialization.XmlSerializer> doit sérialiser dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="2faba-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="2faba-113">Les attributs disponibles sont : <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> et <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2faba-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="2faba-114">Donnez à la propriété `Namespace` de chaque attribut l'une des valeurs d'espace de noms de `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="2faba-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="2faba-115">Passez `XmlSerializerNamespaces` à la méthode `Serialize` de `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="2faba-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="2faba-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="2faba-116">Example</span></span>

<span data-ttu-id="2faba-117">L'exemple suivant crée un `XmlSerializerNamespaces` et ajoute deux paires préfixe/espace de noms à l'objet.</span><span class="sxs-lookup"><span data-stu-id="2faba-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="2faba-118">Le code crée un `XmlSerializer` utilisé pour sérialiser une instance de la classe `Books`.</span><span class="sxs-lookup"><span data-stu-id="2faba-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="2faba-119">Le code appelle la méthode `Serialize` avec `XmlSerializerNamespaces`, ce qui permet au code XML de contenir des espaces de noms préfixés.</span><span class="sxs-lookup"><span data-stu-id="2faba-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }
    
    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a><span data-ttu-id="2faba-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2faba-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="2faba-121">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="2faba-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="2faba-122">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="2faba-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="2faba-123">Classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="2faba-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="2faba-124">Attributs qui contrôlent la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="2faba-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="2faba-125">Guide pratique pour spécifier un nom d’élément différent pour un flux XML</span><span class="sxs-lookup"><span data-stu-id="2faba-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="2faba-126">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="2faba-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="2faba-127">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="2faba-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
