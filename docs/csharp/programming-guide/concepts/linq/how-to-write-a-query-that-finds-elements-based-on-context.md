---
title: Comment écrire une requête qui recherche des éléments en fonction du contexte (C#)
description: Découvrez comment écrire une requête qui recherche des éléments en fonction du contexte. Consultez des exemples de code et affichez des ressources supplémentaires.
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 64f09a41c2c1d01b0be8f776461f9be9df9ecb5f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303190"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="06878-104">Comment écrire une requête qui recherche des éléments en fonction du contexte (C#)</span><span class="sxs-lookup"><span data-stu-id="06878-104">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="06878-105">Parfois, vous devez écrire une requête qui sélectionne des éléments en fonction de leur contexte.</span><span class="sxs-lookup"><span data-stu-id="06878-105">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="06878-106">Vous souhaiterez peut-être filtrer en fonction des éléments frères qui précèdent ou qui suivent.</span><span class="sxs-lookup"><span data-stu-id="06878-106">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="06878-107">Vous souhaiterez peut-être filtrer en fonction des éléments enfants ou ancêtres.</span><span class="sxs-lookup"><span data-stu-id="06878-107">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="06878-108">Vous pouvez pour cela écrire une requête et utiliser ses résultats dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="06878-108">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="06878-109">Si vous devez tout d'abord tester par rapport à la valeur Null, puis tester la valeur, il est plus pratique de créer la requête dans une clause `let`, puis d'utiliser les résultats dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="06878-109">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06878-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="06878-110">Example</span></span>  
 <span data-ttu-id="06878-111">L'exemple suivant sélectionne tous les éléments `p` qui sont suivis immédiatement d'un élément `ul`.</span><span class="sxs-lookup"><span data-stu-id="06878-111">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="06878-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="06878-112">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="06878-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="06878-113">Example</span></span>  
 <span data-ttu-id="06878-114">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="06878-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="06878-115">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06878-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="06878-116">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="06878-116">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="06878-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06878-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
