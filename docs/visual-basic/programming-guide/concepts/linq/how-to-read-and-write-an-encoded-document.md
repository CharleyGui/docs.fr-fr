---
title: 'Procédure : lire et écrire un document encodé'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397906"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="71368-102">Comment : lire et écrire un document encodé (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71368-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>

<span data-ttu-id="71368-103">Pour créer un document XML encodé, vous devez ajouter un objet <xref:System.Xml.Linq.XDeclaration> à l'arborescence XML et définir l'encodage au nom de la page de codes souhaitée.</span><span class="sxs-lookup"><span data-stu-id="71368-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="71368-104">Toute valeur retournée par <xref:System.Text.Encoding.WebName%2A> est une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="71368-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="71368-105">Si vous lisez un document encodé, la propriété <xref:System.Xml.Linq.XDeclaration.Encoding%2A> sera définie au nom de la page de codes.</span><span class="sxs-lookup"><span data-stu-id="71368-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="71368-106">Si vous affectez un nom de page de codes valide à <xref:System.Xml.Linq.XDeclaration.Encoding%2A>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sérialise avec l'encodage spécifié.</span><span class="sxs-lookup"><span data-stu-id="71368-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>

## <a name="example"></a><span data-ttu-id="71368-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="71368-107">Example</span></span>

<span data-ttu-id="71368-108">L'exemple suivant crée deux documents, un avec l'encodage utf-8 et l'autre avec l'encodage utf-16.</span><span class="sxs-lookup"><span data-stu-id="71368-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="71368-109">Il charge ensuite les documents et imprime l'encodage sur la console.</span><span class="sxs-lookup"><span data-stu-id="71368-109">It then loads the documents and prints the encoding to the console.</span></span>

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

<span data-ttu-id="71368-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="71368-110">This example produces the following output:</span></span>

```console
Creating a document with utf-8 encoding
Encoding is:utf-8

Creating a document with utf-16 encoding
Encoding is:utf-16

Encoded document:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-8

Encoded document:
<?xml version="1.0" encoding="utf-16" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-16
```

## <a name="see-also"></a><span data-ttu-id="71368-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71368-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="71368-112">Visual Basic (Advanced LINQ to XML Programming)</span><span class="sxs-lookup"><span data-stu-id="71368-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
