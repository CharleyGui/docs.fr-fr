---
title: Création d’arborescences XML en C# (LINQ to XML)
description: En savoir plus sur la création d’arborescences XML en C#, notamment la construction d’éléments et l’utilisation de constructeurs XElement.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3991f461c4c870a64320853ccd1d45026a8a6bf6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105479"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="717b4-103">Création d’arborescences XML en C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="717b4-103">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="717b4-104">Cette section fournit des informations sur la création d’arborescences XML en C#.</span><span class="sxs-lookup"><span data-stu-id="717b4-104">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="717b4-105">Pour plus d’informations sur l’utilisation des résultats de requêtes LINQ comme contenu d’un <xref:System.Xml.Linq.XElement>, consultez [Construction fonctionnelle (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="717b4-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="717b4-106">Construction d’éléments</span><span class="sxs-lookup"><span data-stu-id="717b4-106">Constructing elements</span></span>
 <span data-ttu-id="717b4-107">Les signatures des constructeurs <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute> vous permettent de passer le contenu de l'élément ou attribut en tant qu'arguments du constructeur.</span><span class="sxs-lookup"><span data-stu-id="717b4-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="717b4-108">Étant donné que l’un des constructeurs prend une quantité variable d’arguments, vous pouvez passer une quantité quelconque d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="717b4-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="717b4-109">Bien entendu, chacun de ces éléments enfants peut contenir ses propres éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="717b4-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="717b4-110">Pour tout élément, vous pouvez ajouter une quantité quelconque d'attributs.</span><span class="sxs-lookup"><span data-stu-id="717b4-110">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="717b4-111">Lors de l'ajout d'objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n'a pas de parent, les objets sont simplement attachés à l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="717b4-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="717b4-112">Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="717b4-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="717b4-113">Ceci est illustré dans le dernier exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="717b4-113">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="717b4-114">Pour créer un objet `contacts`<xref:System.Xml.Linq.XElement>, vous pouvez utiliser le code suivant :</span><span class="sxs-lookup"><span data-stu-id="717b4-114">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="717b4-115">S'il est mis en retrait correctement, le code pour construire des objets <xref:System.Xml.Linq.XElement> ressemble étroitement à la structure du code XML sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="717b4-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="717b4-116">Constructeurs XElement</span><span class="sxs-lookup"><span data-stu-id="717b4-116">XElement constructors</span></span>  
 <span data-ttu-id="717b4-117">La classe <xref:System.Xml.Linq.XElement> utilise les constructeurs suivants pour la construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="717b4-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="717b4-118">Notez qu'il existe d'autres constructeurs pour <xref:System.Xml.Linq.XElement>, mais ils ne sont pas répertoriés ici car ils ne sont pas utilisés pour la construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="717b4-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="717b4-119">Constructeur</span><span class="sxs-lookup"><span data-stu-id="717b4-119">Constructor</span></span>|<span data-ttu-id="717b4-120">Description</span><span class="sxs-lookup"><span data-stu-id="717b4-120">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="717b4-121">Crée un <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="717b4-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="717b4-122">Le paramètre `name` spécifie le nom de l'élément ; `content` spécifie le contenu de l'élément.</span><span class="sxs-lookup"><span data-stu-id="717b4-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="717b4-123">Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="717b4-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="717b4-124">Crée un objet <xref:System.Xml.Linq.XElement> avec son objet <xref:System.Xml.Linq.XName> initialisé au nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="717b4-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="717b4-125">Les attributs et/ou éléments enfants sont créés à partir du contenu de la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="717b4-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="717b4-126">Le paramètre `content` est extrêmement souple.</span><span class="sxs-lookup"><span data-stu-id="717b4-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="717b4-127">Il prend en charge tout type d'objet qui est un enfant valide d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="717b4-127">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="717b4-128">Les règles suivantes s'appliquent à différents types d'objets passés dans ce paramètre :</span><span class="sxs-lookup"><span data-stu-id="717b4-128">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="717b4-129">Une chaîne est ajoutée en tant que contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="717b4-129">A string is added as text content.</span></span>  
  
- <span data-ttu-id="717b4-130">Un objet <xref:System.Xml.Linq.XElement> est ajouté en tant qu'élément enfant.</span><span class="sxs-lookup"><span data-stu-id="717b4-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="717b4-131">Un objet <xref:System.Xml.Linq.XAttribute> est ajouté en tant qu'attribut.</span><span class="sxs-lookup"><span data-stu-id="717b4-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="717b4-132">Un objet <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> est ajouté en tant que contenu enfant.</span><span class="sxs-lookup"><span data-stu-id="717b4-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="717b4-133">Un objet <xref:System.Collections.IEnumerable> est énuméré et ces règles sont appliquées de manière récursive aux résultats.</span><span class="sxs-lookup"><span data-stu-id="717b4-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="717b4-134">Pour tout autre type, sa méthode `ToString` est appelée et le résultat est ajouté en tant que contenu texte.</span><span class="sxs-lookup"><span data-stu-id="717b4-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="717b4-135">Création d’un XElement avec du contenu</span><span class="sxs-lookup"><span data-stu-id="717b4-135">Creating an XElement with content</span></span>  
 <span data-ttu-id="717b4-136">Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple avec un appel de méthode unique.</span><span class="sxs-lookup"><span data-stu-id="717b4-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="717b4-137">Pour cela, spécifiez le contenu comme second paramètre, comme suit :</span><span class="sxs-lookup"><span data-stu-id="717b4-137">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="717b4-138">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-138">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="717b4-139">Vous pouvez passer tout type d'objet en tant que contenu.</span><span class="sxs-lookup"><span data-stu-id="717b4-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="717b4-140">Par exemple, le code suivant crée un élément qui contient un nombre à virgule flottante en tant que contenu :</span><span class="sxs-lookup"><span data-stu-id="717b4-140">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="717b4-141">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-141">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="717b4-142">Le nombre à virgule flottante est boxed et passé au constructeur.</span><span class="sxs-lookup"><span data-stu-id="717b4-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="717b4-143">Le nombre boxed est converti en une chaîne et utilisé comme contenu de l'élément.</span><span class="sxs-lookup"><span data-stu-id="717b4-143">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="717b4-144">Création d’un XElement avec un élément enfant</span><span class="sxs-lookup"><span data-stu-id="717b4-144">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="717b4-145">Si vous passez une instance de la classe <xref:System.Xml.Linq.XElement> comme argument de contenu, le constructeur crée un élément avec un élément enfant :</span><span class="sxs-lookup"><span data-stu-id="717b4-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="717b4-146">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-146">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="717b4-147">Création d’un XElement avec plusieurs éléments enfants</span><span class="sxs-lookup"><span data-stu-id="717b4-147">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="717b4-148">Vous pouvez passer une quantité quelconque d'objets <xref:System.Xml.Linq.XElement> comme contenu.</span><span class="sxs-lookup"><span data-stu-id="717b4-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="717b4-149">Chacun des objets <xref:System.Xml.Linq.XElement> est inclus en tant qu'élément enfant.</span><span class="sxs-lookup"><span data-stu-id="717b4-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="717b4-150">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-150">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="717b4-151">En étendant l'exemple ci-dessus, vous pouvez créer une arborescence XML entière, comme suit :</span><span class="sxs-lookup"><span data-stu-id="717b4-151">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="717b4-152">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-152">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="717b4-153">Créer un XElement avec XAttribute</span><span class="sxs-lookup"><span data-stu-id="717b4-153">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="717b4-154">Si vous passez une instance de la classe <xref:System.Xml.Linq.XAttribute> comme argument de contenu, le constructeur crée un élément avec un attribut :</span><span class="sxs-lookup"><span data-stu-id="717b4-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="717b4-155">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-155">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="717b4-156">Création d’un élément vide</span><span class="sxs-lookup"><span data-stu-id="717b4-156">Creating an empty element</span></span>  
 <span data-ttu-id="717b4-157">Pour créer un objet <xref:System.Xml.Linq.XElement> vide, vous ne passez aucun contenu au constructeur.</span><span class="sxs-lookup"><span data-stu-id="717b4-157">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="717b4-158">L'exemple suivant crée un élément vide :</span><span class="sxs-lookup"><span data-stu-id="717b4-158">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="717b4-159">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="717b4-159">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="717b4-160">Attachement et clonage</span><span class="sxs-lookup"><span data-stu-id="717b4-160">Attaching vs. cloning</span></span>  
 <span data-ttu-id="717b4-161">Comme mentionné précédemment, lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> (y compris <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="717b4-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="717b4-162">Si le nouveau contenu a déjà un parent et fait partie d’une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="717b4-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="717b4-163">L’exemple suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément non apparenté à une arborescence.</span><span class="sxs-lookup"><span data-stu-id="717b4-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="717b4-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="717b4-164">See also</span></span>

- [<span data-ttu-id="717b4-165">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="717b4-165">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
