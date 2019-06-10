---
title: 'Procédure : Effectuer le streaming de fragments XML avec accès aux informations d’en-tête (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 4ecf20134c0d5897418c7667908f80511a962871
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484839"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="49f1a-102">Procédure : Effectuer le streaming de fragments XML avec accès aux informations d’en-tête (C#)</span><span class="sxs-lookup"><span data-stu-id="49f1a-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="49f1a-103">Vous devez parfois lire des fichiers XML arbitrairement volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible.</span><span class="sxs-lookup"><span data-stu-id="49f1a-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="49f1a-104">Si vous tentez de remplir une arborescence XML avec un grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive).</span><span class="sxs-lookup"><span data-stu-id="49f1a-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="49f1a-105">Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.</span><span class="sxs-lookup"><span data-stu-id="49f1a-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="49f1a-106">L'une des options consiste à écrire votre application à l'aide de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="49f1a-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="49f1a-107">Toutefois, vous souhaiterez peut-être utiliser [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour interroger l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="49f1a-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="49f1a-108">Si tel est le cas, vous pouvez écrire votre propre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="49f1a-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="49f1a-109">Pour plus d'informations, voir [Procédure : Écrire une méthode d’axe LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="49f1a-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="49f1a-110">Pour écrire votre propre méthode d'axe personnalisée, vous écrivez une petite méthode qui utilise l'objet <xref:System.Xml.XmlReader> pour lire les nœuds jusqu'à atteindre l'un des nœuds qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="49f1a-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="49f1a-111">La méthode appelle ensuite <xref:System.Xml.Linq.XNode.ReadFrom%2A>, qui lit à partir de l'objet <xref:System.Xml.XmlReader> et instancie un fragment XML.</span><span class="sxs-lookup"><span data-stu-id="49f1a-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="49f1a-112">Elle produit ensuite chaque fragment via `yield return` à la méthode qui énumère votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="49f1a-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="49f1a-113">Vous pouvez ensuite écrire des requêtes LINQ sur votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="49f1a-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="49f1a-114">Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="49f1a-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="49f1a-115">Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="49f1a-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="49f1a-116">Notez que si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="49f1a-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49f1a-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="49f1a-117">Example</span></span>  
 <span data-ttu-id="49f1a-118">Le problème peut parfois être un peu plus épineux.</span><span class="sxs-lookup"><span data-stu-id="49f1a-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="49f1a-119">Dans le document XML suivant, le consommateur de votre méthode d'axe personnalisée doit également connaître le nom du client auquel appartient chaque élément.</span><span class="sxs-lookup"><span data-stu-id="49f1a-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="49f1a-120">L'approche utilisée dans cet exemple consiste à rechercher ces informations d'en-tête, à les enregistrer, puis à générer une petite arborescence XML qui contient à la fois les informations d'en-tête et le détail que vous énumérez.</span><span class="sxs-lookup"><span data-stu-id="49f1a-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="49f1a-121">La méthode d'axe produit ensuite cette nouvelle petite arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="49f1a-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="49f1a-122">La requête a alors accès aux informations d'en-tête et aux informations de détail.</span><span class="sxs-lookup"><span data-stu-id="49f1a-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="49f1a-123">Cette approche présente un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="49f1a-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="49f1a-124">À mesure que chaque fragment XML de détail est produit, aucune référence au fragment précédent n'est conservée et il est disponible pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="49f1a-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="49f1a-125">Notez que cette technique crée de nombreux objets à courte durée de vie sur la pile.</span><span class="sxs-lookup"><span data-stu-id="49f1a-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="49f1a-126">L'exemple suivant montre comment implémenter et utiliser une méthode d'axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par l'URI.</span><span class="sxs-lookup"><span data-stu-id="49f1a-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="49f1a-127">Cet axe personnalisé est écrit spécifiquement de sorte qu'il s'attende à recevoir un document possédant des éléments `Customer`, `Name` et `Item`, et que ces éléments seront disposés comme dans le document `Source.xml` ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="49f1a-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="49f1a-128">Il s'agit d'une implémentation simpliste.</span><span class="sxs-lookup"><span data-stu-id="49f1a-128">It is a simplistic implementation.</span></span> <span data-ttu-id="49f1a-129">Une implémentation plus robuste serait préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="49f1a-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="49f1a-130">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="49f1a-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
  