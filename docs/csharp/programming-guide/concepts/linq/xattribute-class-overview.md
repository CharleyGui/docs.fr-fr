---
title: Vue d’ensemble de la classe XAttribute (C#)
description: Les attributs sont des paires nom/valeur associées à un élément. XAttribute représente des attributs XML. En savoir plus sur l’utilisation des attributs dans LINQ to XML en C#.
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302228"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="cf967-105">Vue d’ensemble de la classe XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="cf967-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="cf967-106">Les attributs sont des paires nom/valeur associées à un élément.</span><span class="sxs-lookup"><span data-stu-id="cf967-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="cf967-107">La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="cf967-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cf967-108">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="cf967-108">Overview</span></span>  
 <span data-ttu-id="cf967-109">L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est semblable à l'utilisation des éléments.</span><span class="sxs-lookup"><span data-stu-id="cf967-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="cf967-110">Leurs constructeurs sont similaires.</span><span class="sxs-lookup"><span data-stu-id="cf967-110">Their constructors are similar.</span></span> <span data-ttu-id="cf967-111">Les méthodes que vous utilisez pour en récupérer des collections sont similaires.</span><span class="sxs-lookup"><span data-stu-id="cf967-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="cf967-112">Une expression de requête LINQ pour une collection d’attributs a une apparence très semblable à une expression de requête LINQ pour une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="cf967-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="cf967-113">L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé.</span><span class="sxs-lookup"><span data-stu-id="cf967-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="cf967-114">Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="cf967-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="cf967-115">Le constructeur XAttribute</span><span class="sxs-lookup"><span data-stu-id="cf967-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="cf967-116">Le constructeur suivant de la classe <xref:System.Xml.Linq.XAttribute> est celui que vous utiliserez le plus souvent :</span><span class="sxs-lookup"><span data-stu-id="cf967-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="cf967-117">Constructeur</span><span class="sxs-lookup"><span data-stu-id="cf967-117">Constructor</span></span>|<span data-ttu-id="cf967-118">Description</span><span class="sxs-lookup"><span data-stu-id="cf967-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="cf967-119">Crée un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cf967-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="cf967-120">L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="cf967-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="cf967-121">Création d'un élément avec un attribut</span><span class="sxs-lookup"><span data-stu-id="cf967-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="cf967-122">Le code suivant illustre la tâche courante de création d’un élément qui contient un attribut :</span><span class="sxs-lookup"><span data-stu-id="cf967-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="cf967-123">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cf967-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="cf967-124">Construction fonctionnelle d'attributs</span><span class="sxs-lookup"><span data-stu-id="cf967-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="cf967-125">Vous pouvez construire des objets <xref:System.Xml.Linq.XAttribute> en ligne avec la construction d'objets <xref:System.Xml.Linq.XElement> de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="cf967-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="cf967-126">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cf967-126">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="cf967-127">Les attributs ne sont pas des nœuds</span><span class="sxs-lookup"><span data-stu-id="cf967-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="cf967-128">Il existe certaines différences entre les attributs et les éléments.</span><span class="sxs-lookup"><span data-stu-id="cf967-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="cf967-129">Les objets <xref:System.Xml.Linq.XAttribute> ne sont pas des nœuds dans l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="cf967-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="cf967-130">Il s'agit de paires nom/valeur associées à un élément XML.</span><span class="sxs-lookup"><span data-stu-id="cf967-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="cf967-131">Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML.</span><span class="sxs-lookup"><span data-stu-id="cf967-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="cf967-132">Bien que les objets <xref:System.Xml.Linq.XAttribute> ne soient pas réellement des nœuds de l'arborescence XML, l'utilisation d'objets <xref:System.Xml.Linq.XAttribute> s'apparente à l'utilisation d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cf967-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cf967-133">Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud.</span><span class="sxs-lookup"><span data-stu-id="cf967-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="cf967-134">De nombreux développeurs n'auront pas à se sourcier de cette distinction.</span><span class="sxs-lookup"><span data-stu-id="cf967-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf967-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf967-135">See also</span></span>

- [<span data-ttu-id="cf967-136">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="cf967-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
