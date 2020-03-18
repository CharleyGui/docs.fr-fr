---
title: Comment effectuer la transformation en streaming de grands documents XML (C)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 9eb2e832f798e550ef3b534b0c9a0e3416378b43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169102"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="f2a72-102">Comment effectuer la transformation en streaming de grands documents XML (C)</span><span class="sxs-lookup"><span data-stu-id="f2a72-102">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="f2a72-103">Vous devez parfois transformer des fichiers XML volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible.</span><span class="sxs-lookup"><span data-stu-id="f2a72-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="f2a72-104">Si vous tentez de remplir une arborescence XML avec un très grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive).</span><span class="sxs-lookup"><span data-stu-id="f2a72-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="f2a72-105">Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.</span><span class="sxs-lookup"><span data-stu-id="f2a72-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="f2a72-106">Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="f2a72-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="f2a72-107">Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="f2a72-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="f2a72-108">Notez que si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="f2a72-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="f2a72-109">Même si vous utilisez la technique décrite dans [Comment diffuser des fragments de XML avec accès à des informations d’en-tête (](./how-to-stream-xml-fragments-with-access-to-header-information.md)si vous essayez d’assembler un arbre XML qui contient le document transformé, l’utilisation de la mémoire sera trop grande.</span><span class="sxs-lookup"><span data-stu-id="f2a72-109">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="f2a72-110">Il existe deux approches principales.</span><span class="sxs-lookup"><span data-stu-id="f2a72-110">There are two main approaches.</span></span> <span data-ttu-id="f2a72-111">L'une d'elles consiste à utiliser les caractéristiques de traitement différé de <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="f2a72-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="f2a72-112">Une autre consiste à créer un objet <xref:System.Xml.XmlWriter> et à utiliser les fonctionnalités de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour écrire des éléments dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2a72-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f2a72-113">Cette rubrique illustre les deux approches.</span><span class="sxs-lookup"><span data-stu-id="f2a72-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a72-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f2a72-114">Example</span></span>  
 <span data-ttu-id="f2a72-115">L’exemple suivant s’appuie sur l’exemple dans [Comment diffuser des fragments de XML avec accès à des informations d’en-tête ( C.](./how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="f2a72-115">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="f2a72-116">Il utilise les capacités d'exécution différée de <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu.</span><span class="sxs-lookup"><span data-stu-id="f2a72-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="f2a72-117">Cet exemple peut transformer un document de grande taille tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2a72-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="f2a72-118">Notez que l'axe personnalisé (`StreamCustomerItem`) est spécifiquement écrit de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document  Source.xml suivant.</span><span class="sxs-lookup"><span data-stu-id="f2a72-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="f2a72-119">Une implémentation plus robuste serait toutefois préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="f2a72-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="f2a72-120">Voici le document source, Source.xml :</span><span class="sxs-lookup"><span data-stu-id="f2a72-120">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="f2a72-121">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f2a72-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f2a72-122"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f2a72-122">Example</span></span>  
<span data-ttu-id="f2a72-123">L’exemple suivant s’appuie également sur l’exemple dans [Comment diffuser des fragments de XML avec accès à des informations d’en-tête ( C.](./how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="f2a72-123">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="f2a72-124">Il utilise la fonctionnalité de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour écrire des éléments dans un <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2a72-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f2a72-125">Cet exemple peut transformer un document de grande taille tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2a72-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="f2a72-126">Notez que l'axe personnalisé (`StreamCustomerItem`) est spécifiquement écrit de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document  Source.xml suivant.</span><span class="sxs-lookup"><span data-stu-id="f2a72-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="f2a72-127">Une implémentation plus robuste, toutefois, validerait le document source avec un fichier XSD ou serait préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="f2a72-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="f2a72-128">Cet exemple utilise le même document source, Source.xml, que l'exemple précédent dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f2a72-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="f2a72-129">Il produit également exactement la même sortie.</span><span class="sxs-lookup"><span data-stu-id="f2a72-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="f2a72-130">L'utilisation de l'objet <xref:System.Xml.Linq.XStreamingElement> pour diffuser en continu le code XML de sortie est préférable à l'écriture dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f2a72-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="f2a72-131">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f2a72-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  