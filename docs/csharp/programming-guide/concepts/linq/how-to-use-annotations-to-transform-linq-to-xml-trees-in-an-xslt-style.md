---
title: Comment utiliser des annotations pour transformer les arbres LINQ en arbres XML dans un style XSLT (C)
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 7d6d646bb9b7b344750c22cb24bc81999da5210d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168555"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="a34c9-102">Comment utiliser des annotations pour transformer les arbres LINQ en arbres XML dans un style XSLT (C)</span><span class="sxs-lookup"><span data-stu-id="a34c9-102">How to use annotations to transform LINQ to XML trees in an XSLT style (C#)</span></span>
<span data-ttu-id="a34c9-103">Les annotations peuvent servir à faciliter les transformations d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="a34c9-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="a34c9-104">Certains documents XML sont « centrés sur les documents avec du contenu mixte ».</span><span class="sxs-lookup"><span data-stu-id="a34c9-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="a34c9-105">Avec ces documents, vous ne connaissez pas nécessairement la forme des enfants nœuds d'un élément.</span><span class="sxs-lookup"><span data-stu-id="a34c9-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="a34c9-106">Par exemple, un nœud qui contient du texte peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="a34c9-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="a34c9-107">Pour tout nœud de texte donné, il peut exister une quantité quelconque d'éléments enfants `<b>` et `<i>`.</span><span class="sxs-lookup"><span data-stu-id="a34c9-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="a34c9-108">Cette approche s’étend à plusieurs autres situations, par exemple à des pages qui contiennent une variété d’éléments enfants, tels que des paragraphes normaux, des paragraphes à puces et des bitmaps.</span><span class="sxs-lookup"><span data-stu-id="a34c9-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="a34c9-109">Les cellules d’un tableau peuvent contenir du texte, des listes déroulantes ou des bitmaps.</span><span class="sxs-lookup"><span data-stu-id="a34c9-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="a34c9-110">L'une des principales caractéristiques du code XML centré sur les documents est que vous ne savez pas quel élément enfant un élément particulier aura.</span><span class="sxs-lookup"><span data-stu-id="a34c9-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="a34c9-111">Si vous souhaitez transformer des éléments d'une arborescence dans laquelle vous ne connaissez pas forcément grand chose des enfants des éléments que vous souhaitez transformer, cette approche qui utilise des annotations est une approche efficace.</span><span class="sxs-lookup"><span data-stu-id="a34c9-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="a34c9-112">La synthèse de l'approche est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a34c9-112">The summary of the approach is:</span></span>  
  
- <span data-ttu-id="a34c9-113">Tout d'abord, annotez les éléments de l'arborescence avec un élément de remplacement.</span><span class="sxs-lookup"><span data-stu-id="a34c9-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
- <span data-ttu-id="a34c9-114">Ensuite, itérez l'ensemble de l'arborescence et créez une nouvelle arborescence où vous remplacez chaque élément par son annotation.</span><span class="sxs-lookup"><span data-stu-id="a34c9-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="a34c9-115">Cet exemple implémente l'itération et la création de la nouvelle arborescence dans une fonction nommée `XForm`.</span><span class="sxs-lookup"><span data-stu-id="a34c9-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="a34c9-116">En détail, l'approche se compose des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a34c9-116">In detail, the approach consists of:</span></span>  
  
- <span data-ttu-id="a34c9-117">Exécutez une ou plusieurs requêtes LINQ to XML qui retournent l'ensemble d'éléments que vous souhaitez transformer d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="a34c9-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="a34c9-118">Pour chaque élément dans la requête, ajoutez un nouvel objet <xref:System.Xml.Linq.XElement> en tant qu'annotation de l'élément.</span><span class="sxs-lookup"><span data-stu-id="a34c9-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="a34c9-119">Ce nouvel élément remplacera l’élément annoté dans la nouvelle arborescence transformée.</span><span class="sxs-lookup"><span data-stu-id="a34c9-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="a34c9-120">Ce code est simple à écrire, comme illustré dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a34c9-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
- <span data-ttu-id="a34c9-121">Le nouvel élément ajouté en tant qu'annotation peut contenir de nouveaux nœuds enfants ; il peut former une sous-arborescence de toute forme souhaitée.</span><span class="sxs-lookup"><span data-stu-id="a34c9-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
- <span data-ttu-id="a34c9-122">Il existe une règle spéciale : si un nœud enfant du nouvel élément est dans un espace de noms différent, un espace de noms créé à cet effet (dans cet exemple, l'espace de noms est `http://www.microsoft.com/LinqToXmlTransform/2007`), cet élément enfant n'est pas copié dans la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="a34c9-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="a34c9-123">Au lieu de cela, si l'espace de noms est l'espace de noms spécial mentionné ci-dessus et que le nom local de l'élément est `ApplyTransforms`, les nœuds enfants de l'élément dans l'arborescence source sont itérés et copiés dans la nouvelle arborescence (hormis le fait que les éléments enfants annotés sont eux-mêmes transformés conformément à ces règles).</span><span class="sxs-lookup"><span data-stu-id="a34c9-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
- <span data-ttu-id="a34c9-124">Cela est quelque peu analogue à la spécification des transformations en XSL.</span><span class="sxs-lookup"><span data-stu-id="a34c9-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="a34c9-125">La requête qui sélectionne un ensemble de nœuds est analogue à l'expression XPath pour un modèle.</span><span class="sxs-lookup"><span data-stu-id="a34c9-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="a34c9-126">Le code permettant de créer le nouvel objet <xref:System.Xml.Linq.XElement> qui est enregistré en tant qu'annotation est analogue au constructeur de séquence en XSL et l'élément `ApplyTransforms` est analogue en termes de fonction à l'élément `xsl:apply-templates` en XSL.</span><span class="sxs-lookup"><span data-stu-id="a34c9-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
- <span data-ttu-id="a34c9-127">L’un des avantages offerts par cette approche est que lorsque vous formulez des requêtes, vous écrivez toujours des requêtes sur l’arborescence source non modifiée.</span><span class="sxs-lookup"><span data-stu-id="a34c9-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="a34c9-128">Vous n'avez pas à vous soucier de l'impact des modifications apportées à l'arborescence sur les requêtes que vous écrivez.</span><span class="sxs-lookup"><span data-stu-id="a34c9-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="a34c9-129">Transformation d'une arborescence</span><span class="sxs-lookup"><span data-stu-id="a34c9-129">Transforming a Tree</span></span>  
 <span data-ttu-id="a34c9-130">Ce premier exemple renomme tous les nœuds `Paragraph` à `para`.</span><span class="sxs-lookup"><span data-stu-id="a34c9-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement root = XElement.Parse(@"  
<Root>  
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
    <Paragraph>More text.</Paragraph>  
</Root>");  
  
// replace Paragraph with para  
foreach (var el in root.Descendants("Paragraph"))  
    el.AddAnnotation(  
        new XElement("para",  
            // same idea as xsl:apply-templates  
            new XElement(xf + "ApplyTransforms")  
        )  
    );  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 <span data-ttu-id="a34c9-131">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a34c9-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="a34c9-132">Une transformation plus compliquée</span><span class="sxs-lookup"><span data-stu-id="a34c9-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="a34c9-133">L'exemple suivant interroge l'arborescence et calcule la moyenne et la somme des éléments `Data`, puis les ajoute à l'arborescence en tant que nouveaux éléments.</span><span class="sxs-lookup"><span data-stu-id="a34c9-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average", $"{avg:F4}"),
        new XElement("Sum",  
            data  
            .Elements("Data")  
            .Select(z => (int)z)  
            .Sum()  
        )  
    )  
);  
  
Console.WriteLine("Before Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(data);  
Console.WriteLine();  
Console.WriteLine();  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="a34c9-134">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a34c9-134">This example produces the following output:</span></span>  
  
```output  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a><span data-ttu-id="a34c9-135">Réalisation de la transformation</span><span class="sxs-lookup"><span data-stu-id="a34c9-135">Effecting the Transform</span></span>  
 <span data-ttu-id="a34c9-136">Une petite fonction, `XForm`, crée une nouvelle arborescence transformée à partir de l'arborescence d'origine annotée.</span><span class="sxs-lookup"><span data-stu-id="a34c9-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
- <span data-ttu-id="a34c9-137">Le pseudo code de la fonction est assez simple :</span><span class="sxs-lookup"><span data-stu-id="a34c9-137">The pseudo code for the function is quite simple:</span></span>  
  
```text  
The function takes an XElement as an argument and returns an XElement.
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="a34c9-138">Voici l'implémentation de cette fonction :</span><span class="sxs-lookup"><span data-stu-id="a34c9-138">Following is the implementation of this function:</span></span>  
  
```csharp  
// Build a transformed XML tree per the annotations  
static XElement XForm(XElement source)  
{  
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    XName at = xf + "ApplyTransforms";  
  
    if (source.Annotation<XElement>() != null)  
    {  
        XElement anno = source.Annotation<XElement>();  
        return new XElement(anno.Name,  
            anno.Attributes(),  
            anno  
            .Nodes()  
            .Select(  
                (XNode n) =>  
                {  
                    XElement annoEl = n as XElement;  
                    if (annoEl != null)  
                    {  
                        if (annoEl.Name == at)  
                            return (object)(  
                                source.Nodes()  
                                .Select(  
                                    (XNode n2) =>  
                                    {  
                                        XElement e2 = n2 as XElement;  
                                        if (e2 == null)  
                                            return n2;  
                                        else  
                                            return XForm(e2);  
                                    }  
                                )  
                            );  
                        else  
                            return n;  
                    }  
                    else  
                        return n;  
                }  
            )  
        );  
    }  
    else  
    {  
        return new XElement(source.Name,  
            source.Attributes(),  
            source  
                .Nodes()  
                .Select(n =>  
                {  
                    XElement el = n as XElement;  
                    if (el == null)  
                        return n;  
                    else  
                        return XForm(el);  
                }  
                )  
        );  
    }  
}
```  
  
## <a name="complete-example"></a><span data-ttu-id="a34c9-139">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="a34c9-139">Complete Example</span></span>  
 <span data-ttu-id="a34c9-140">Le code suivant est un exemple complet qui inclut la fonction `XForm`.</span><span class="sxs-lookup"><span data-stu-id="a34c9-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="a34c9-141">Il comprend certaines des utilisations courantes de ce type de transformation :</span><span class="sxs-lookup"><span data-stu-id="a34c9-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Xml;  
using System.Xml.Linq;  
  
class Program  
{  
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    static XName at = xf + "ApplyTransforms";  
  
    // Build a transformed XML tree per the annotations  
    static XElement XForm(XElement source)  
    {  
        if (source.Annotation<XElement>() != null)  
        {  
            XElement anno = source.Annotation<XElement>();  
            return new XElement(anno.Name,  
                anno.Attributes(),  
                anno  
                .Nodes()  
                .Select(  
                    (XNode n) =>  
                    {  
                        XElement annoEl = n as XElement;  
                        if (annoEl != null)  
                        {  
                            if (annoEl.Name == at)  
                                return (object)(  
                                    source.Nodes()  
                                    .Select(  
                                        (XNode n2) =>  
                                        {  
                                            XElement e2 = n2 as XElement;  
                                            if (e2 == null)  
                                                return n2;  
                                            else  
                                                return XForm(e2);  
                                        }  
                                    )  
                                );  
                            else  
                                return n;  
                        }  
                        else  
                            return n;  
                    }  
                )  
            );  
        }  
        else  
        {  
            return new XElement(source.Name,  
                source.Attributes(),  
                source  
                    .Nodes()  
                    .Select(n =>  
                    {  
                        XElement el = n as XElement;  
                        if (el == null)  
                            return n;  
                        else  
                            return XForm(el);  
                    }  
                    )  
            );  
        }  
    }  
  
    static void Main(string[] args)  
    {  
        XElement root = new XElement("Root",  
            new XComment("A comment"),  
            new XAttribute("Att1", 123),  
            new XElement("Child", 1),  
            new XElement("Child", 2),  
            new XElement("Other",  
                new XElement("GC", 3),  
                new XElement("GC", 4)  
            ),  
            XElement.Parse(  
              "<SomeMixedContent>This is <i>an</i> element that " +  
              "<b>has</b> some mixed content</SomeMixedContent>"),  
            new XElement("AnUnchangedElement", 42)  
        );  
  
        // each of the following serves the same semantic purpose as  
        // XSLT templates and sequence constructors  
  
        // replace Child with NewChild  
        foreach (var el in root.Elements("Child"))  
            el.AddAnnotation(new XElement("NewChild", (string)el));  
  
        // replace first GC with GrandChild, add an attribute  
        foreach (var el in root.Descendants("GC").Take(1))  
            el.AddAnnotation(  
                new XElement("GrandChild",  
                    new XAttribute("ANewAttribute", 999),  
                    (string)el  
                )  
            );  
  
        // replace Other with NewOther, add new child elements around original content  
        foreach (var el in root.Elements("Other"))  
            el.AddAnnotation(  
                new XElement("NewOther",  
                    new XElement("MyNewChild", 1),  
                    // same idea as xsl:apply-templates  
                    new XElement(xf + "ApplyTransforms"),  
                    new XElement("ChildThatComesAfter")  
                )  
            );  
  
        // change name of element that has mixed content  
        root.Descendants("SomeMixedContent").First().AddAnnotation(  
            new XElement("MixedContent",  
                new XElement(xf + "ApplyTransforms")  
            )  
        );  
  
        // replace <b> with <Bold>  
        foreach (var el in root.Descendants("b"))  
            el.AddAnnotation(  
                new XElement("Bold",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        // replace <i> with <Italic>  
        foreach (var el in root.Descendants("i"))  
            el.AddAnnotation(  
                new XElement("Italic",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        Console.WriteLine("Before Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(root);  
        Console.WriteLine();  
        Console.WriteLine();  
        XElement newRoot = XForm(root);  
  
        Console.WriteLine("After Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(newRoot);  
    }  
}  
```  
  
 <span data-ttu-id="a34c9-142">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a34c9-142">This example produces the following output:</span></span>  
  
```output  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  