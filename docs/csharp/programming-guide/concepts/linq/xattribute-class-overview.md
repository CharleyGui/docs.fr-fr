---
title: Vue d’ensemble de la classe XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635663"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="ff547-102">Vue d’ensemble de la classe XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="ff547-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="ff547-103">Les attributs sont des paires nom/valeur associées à un élément.</span><span class="sxs-lookup"><span data-stu-id="ff547-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="ff547-104">La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="ff547-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ff547-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="ff547-105">Overview</span></span>  
 <span data-ttu-id="ff547-106">L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est semblable à l'utilisation des éléments.</span><span class="sxs-lookup"><span data-stu-id="ff547-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="ff547-107">Leurs constructeurs sont similaires.</span><span class="sxs-lookup"><span data-stu-id="ff547-107">Their constructors are similar.</span></span> <span data-ttu-id="ff547-108">Les méthodes que vous utilisez pour en récupérer des collections sont similaires.</span><span class="sxs-lookup"><span data-stu-id="ff547-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="ff547-109">Une expression de requête LINQ pour une collection d’attributs ressemble beaucoup à une expression de requête LINQ pour une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="ff547-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="ff547-110">L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé.</span><span class="sxs-lookup"><span data-stu-id="ff547-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="ff547-111">Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="ff547-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="ff547-112">Le constructeur XAttribute</span><span class="sxs-lookup"><span data-stu-id="ff547-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="ff547-113">Le constructeur suivant de la classe <xref:System.Xml.Linq.XAttribute> est celui que vous utiliserez le plus souvent :</span><span class="sxs-lookup"><span data-stu-id="ff547-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="ff547-114">Constructeur</span><span class="sxs-lookup"><span data-stu-id="ff547-114">Constructor</span></span>|<span data-ttu-id="ff547-115">Description</span><span class="sxs-lookup"><span data-stu-id="ff547-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="ff547-116">Crée un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ff547-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="ff547-117">L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="ff547-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="ff547-118">Création d'un élément avec un attribut</span><span class="sxs-lookup"><span data-stu-id="ff547-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="ff547-119">Le code suivant illustre la tâche courante de création d’un élément qui contient un attribut :</span><span class="sxs-lookup"><span data-stu-id="ff547-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="ff547-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ff547-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="ff547-121">Construction fonctionnelle d'attributs</span><span class="sxs-lookup"><span data-stu-id="ff547-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="ff547-122">Vous pouvez construire des objets <xref:System.Xml.Linq.XAttribute> en ligne avec la construction d'objets <xref:System.Xml.Linq.XElement> de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="ff547-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="ff547-123">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ff547-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="ff547-124">Les attributs ne sont pas des nœuds</span><span class="sxs-lookup"><span data-stu-id="ff547-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="ff547-125">Il existe certaines différences entre les attributs et les éléments.</span><span class="sxs-lookup"><span data-stu-id="ff547-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="ff547-126">Les objets <xref:System.Xml.Linq.XAttribute> ne sont pas des nœuds dans l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="ff547-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="ff547-127">Il s'agit de paires nom/valeur associées à un élément XML.</span><span class="sxs-lookup"><span data-stu-id="ff547-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="ff547-128">Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML.</span><span class="sxs-lookup"><span data-stu-id="ff547-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="ff547-129">Bien que les objets <xref:System.Xml.Linq.XAttribute> ne soient pas réellement des nœuds de l'arborescence XML, l'utilisation d'objets <xref:System.Xml.Linq.XAttribute> s'apparente à l'utilisation d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ff547-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="ff547-130">Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud.</span><span class="sxs-lookup"><span data-stu-id="ff547-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="ff547-131">De nombreux développeurs n'auront pas à se sourcier de cette distinction.</span><span class="sxs-lookup"><span data-stu-id="ff547-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff547-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff547-132">See also</span></span>

- [<span data-ttu-id="ff547-133">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ff547-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
