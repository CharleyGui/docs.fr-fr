---
title: "Comment : qualifier des noms d'éléments XML et des noms d'attributs XML"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 1f79caf6ff295d793c615b17d387cdd165e440e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353102"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>Comment : qualifier des noms d'éléments XML et des noms d'attributs XML

XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).

Les espaces de noms XML offrent une méthode permettant de qualifier les noms d'éléments et d'attributs XML dans des documents XML. Un nom qualifié se compose d'un préfixe et d'un nom local, séparés par le caractère deux-points. Le préfixe joue uniquement le rôle d'espace réservé ; il est mappé à un URI (Universal Resource Identifier) qui spécifie un espace de noms. L'association entre l'espace de noms URI géré de manière universelle et le nom local génère un nom dont l'unicité universelle est garantie.

En créant une instance de `XmlSerializerNamespaces` et en ajoutant les paires d'espaces de noms à l'objet, vous pouvez spécifier les préfixes utilisés dans un document XML.

## <a name="to-create-qualified-names-in-an-xml-document"></a>Pour créer des noms qualifiés dans un document XML

1. Créez une instance de la classe `XmlSerializerNamespaces`.

2. Ajoutez tous les préfixes et paires d'espaces de noms à `XmlSerializerNamespaces`.

3. Appliquez l'attribut `System.Xml.Serialization` approprié à chaque membre ou classe que <xref:System.Xml.Serialization.XmlSerializer> doit sérialiser dans un document XML.

    Les attributs disponibles sont : <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> et <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Donnez à la propriété `Namespace` de chaque attribut l'une des valeurs d'espace de noms de `XmlSerializerNamespaces`.

5. Passez `XmlSerializerNamespaces` à la méthode `Serialize` de `XmlSerializer`.

## <a name="example"></a>Exemple

L'exemple suivant crée un `XmlSerializerNamespaces` et ajoute deux paires préfixe/espace de noms à l'objet. Le code crée un `XmlSerializer` utilisé pour sérialiser une instance de la classe `Books`. Le code appelle la méthode `Serialize` avec `XmlSerializerNamespaces`, ce qui permet au code XML de contenir des espaces de noms préfixés.

<!-- TODO: THE FOLLOWING VB SNIPPET ISN'T CORRECT!! -->
```vb
Option Explicit
public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}

Option Strict

Imports System
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Class Run

    Public Shared Sub Main()
        Dim test As New Run()
        test.SerializeObject("XmlNamespaces.xml")
    End Sub 'Main

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
End Class

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class 'Books

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
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _
        price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeObject("XmlNamespaces.xml");
    }
    public void SerializeObject(string filename)
    {
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        XmlSerializerNamespaces myNamespaces =
        new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        Book myBook = new Book();
        myBook.TITLE = "A Book Title";
        Price myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        Books myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);
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
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Serialization.XmlSerializer>
- [Outil XML Schema Definition et sérialisation XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Introduction à la sérialisation XML](introducing-xml-serialization.md)
- [XmlSerializer Class](xref:System.Xml.Serialization.XmlSerializer)
- [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md)
- [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md)
