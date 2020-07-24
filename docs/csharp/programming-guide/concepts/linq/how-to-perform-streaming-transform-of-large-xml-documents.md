---
title: Comment effectuer une transformation de diffusion en continu de documents XML volumineux (C#)
description: Apprenez à effectuer une transformation de streaming de texte en XML en C# pour éviter une utilisation excessive de la mémoire pour certains fichiers.
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: e1ab2866079b2244dc764271d7ba63173349e2f3
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104859"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="a390c-103">Comment effectuer une transformation de diffusion en continu de documents XML volumineux (C#)</span><span class="sxs-lookup"><span data-stu-id="a390c-103">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="a390c-104">Vous devez parfois transformer des fichiers XML volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible.</span><span class="sxs-lookup"><span data-stu-id="a390c-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="a390c-105">Si vous tentez de remplir une arborescence XML avec un très grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive).</span><span class="sxs-lookup"><span data-stu-id="a390c-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="a390c-106">Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.</span><span class="sxs-lookup"><span data-stu-id="a390c-106">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="a390c-107">Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="a390c-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="a390c-108">Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="a390c-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="a390c-109">Notez que si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="a390c-109">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="a390c-110">Même si vous utilisez la technique décrite dans Guide pratique [pour diffuser des fragments XML en continu avec accès aux informations d’en-tête (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), si vous essayez d’assembler une arborescence XML qui contient le document transformé, l’utilisation de la mémoire est trop importante.</span><span class="sxs-lookup"><span data-stu-id="a390c-110">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="a390c-111">Il existe deux approches principales.</span><span class="sxs-lookup"><span data-stu-id="a390c-111">There are two main approaches.</span></span> <span data-ttu-id="a390c-112">L'une d'elles consiste à utiliser les caractéristiques de traitement différé de <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="a390c-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="a390c-113">Une autre consiste à créer un objet <xref:System.Xml.XmlWriter> et à utiliser les fonctionnalités de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour écrire des éléments dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a390c-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a390c-114">Cette rubrique illustre les deux approches.</span><span class="sxs-lookup"><span data-stu-id="a390c-114">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a390c-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="a390c-115">Example</span></span>  
 <span data-ttu-id="a390c-116">L’exemple suivant repose sur l’exemple de [diffusion en continu de fragments XML avec accès aux informations d’en-tête (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="a390c-116">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="a390c-117">Il utilise les capacités d'exécution différée de <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu.</span><span class="sxs-lookup"><span data-stu-id="a390c-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="a390c-118">Cet exemple peut transformer un document de grande taille tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="a390c-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="a390c-119">Notez que l'axe personnalisé (`StreamCustomerItem`) est spécifiquement écrit de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document  Source.xml suivant.</span><span class="sxs-lookup"><span data-stu-id="a390c-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="a390c-120">Une implémentation plus robuste serait toutefois préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="a390c-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="a390c-121">Voici le document source, Source.xml :</span><span class="sxs-lookup"><span data-stu-id="a390c-121">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="a390c-122">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a390c-122">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a390c-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="a390c-123">Example</span></span>  
<span data-ttu-id="a390c-124">L’exemple suivant s’appuie également sur l’exemple dans [Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="a390c-124">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="a390c-125">Il utilise la fonctionnalité de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour écrire des éléments dans un <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a390c-125">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a390c-126">Cet exemple peut transformer un document de grande taille tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="a390c-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="a390c-127">Notez que l'axe personnalisé (`StreamCustomerItem`) est spécifiquement écrit de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document  Source.xml suivant.</span><span class="sxs-lookup"><span data-stu-id="a390c-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="a390c-128">Une implémentation plus robuste, toutefois, validerait le document source avec un fichier XSD ou serait préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="a390c-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="a390c-129">Cet exemple utilise le même document source, Source.xml, que l'exemple précédent dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a390c-129">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="a390c-130">Il produit également exactement la même sortie.</span><span class="sxs-lookup"><span data-stu-id="a390c-130">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="a390c-131">L'utilisation de l'objet <xref:System.Xml.Linq.XStreamingElement> pour diffuser en continu le code XML de sortie est préférable à l'écriture dans un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="a390c-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="a390c-132">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a390c-132">This code produces the following output:</span></span>  
  
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
  