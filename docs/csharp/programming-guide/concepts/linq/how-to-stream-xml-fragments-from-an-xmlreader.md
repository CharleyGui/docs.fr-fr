---
title: Comment diffuser des fragments XML en continu à partir d’un XmlReader (C#)
description: Découvrez comment diffuser en continu des fragments XML à partir d’un XmlReader. Cette méthode est utilisée pour le traitement des fichiers XML volumineux.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301019"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="8ef53-104">Comment diffuser des fragments XML en continu à partir d’un XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="8ef53-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="8ef53-105">Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="8ef53-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="8ef53-106">Cette rubrique montre comment diffuser des fragments en continu à l'aide d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="8ef53-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="8ef53-107">L'une des manières les plus efficaces d'utiliser un objet <xref:System.Xml.XmlReader> pour lire des objets <xref:System.Xml.Linq.XElement> consiste à écrire votre propre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ef53-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="8ef53-108">Une méthode d'axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, comme illustré dans l'exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8ef53-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="8ef53-109">Dans la méthode d'axe personnalisée, après avoir créé le fragment XML en appelant la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retournez la collection à l'aide de `yield return`.</span><span class="sxs-lookup"><span data-stu-id="8ef53-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="8ef53-110">Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ef53-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="8ef53-111">Lorsque vous créez une arborescence XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> doit être positionné sur un élément.</span><span class="sxs-lookup"><span data-stu-id="8ef53-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="8ef53-112">La méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A> ne retourne que lorsqu'elle a lu la balise de fermeture de l'élément.</span><span class="sxs-lookup"><span data-stu-id="8ef53-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="8ef53-113">Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un objet <xref:System.Xml.XmlReader>, positionner le lecteur sur le nœud que vous souhaitez convertir en une arborescence <xref:System.Xml.Linq.XElement>, puis créer l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8ef53-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="8ef53-114">La rubrique Guide pratique [pour diffuser des fragments XML en continu avec accès aux informations d’en-tête (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la façon de diffuser un document plus complexe.</span><span class="sxs-lookup"><span data-stu-id="8ef53-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="8ef53-115">La rubrique Guide pratique [pour effectuer une transformation de diffusion en continu de documents XML volumineux (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="8ef53-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ef53-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ef53-116">Example</span></span>  
 <span data-ttu-id="8ef53-117">Cet exemple crée une méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ef53-117">This example creates a custom axis method.</span></span> <span data-ttu-id="8ef53-118">Vous pouvez l’interroger à l’aide d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="8ef53-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="8ef53-119">La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.</span><span class="sxs-lookup"><span data-stu-id="8ef53-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="8ef53-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8ef53-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="8ef53-121">Dans cet exemple, le document source est très petit.</span><span class="sxs-lookup"><span data-stu-id="8ef53-121">In this example, the source document is very small.</span></span> <span data-ttu-id="8ef53-122">Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.</span><span class="sxs-lookup"><span data-stu-id="8ef53-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
