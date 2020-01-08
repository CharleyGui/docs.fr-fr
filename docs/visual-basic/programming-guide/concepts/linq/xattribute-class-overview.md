---
title: Vue d'ensemble de la classe XAttribute
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: ceafe5478e41fb4c2038fd9300ef7b1ee6cb8411
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636651"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="c0aae-102">Vue d’ensemble de la classe XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0aae-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="c0aae-103">Les attributs sont des paires nom/valeur associées à un élément.</span><span class="sxs-lookup"><span data-stu-id="c0aae-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="c0aae-104">La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="c0aae-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c0aae-105">Vue d'ensemble de</span><span class="sxs-lookup"><span data-stu-id="c0aae-105">Overview</span></span>  
 <span data-ttu-id="c0aae-106">L'utilisation des attributs dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est semblable à l'utilisation des éléments.</span><span class="sxs-lookup"><span data-stu-id="c0aae-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="c0aae-107">Leurs constructeurs sont similaires.</span><span class="sxs-lookup"><span data-stu-id="c0aae-107">Their constructors are similar.</span></span> <span data-ttu-id="c0aae-108">Les méthodes que vous utilisez pour en récupérer des collections sont similaires.</span><span class="sxs-lookup"><span data-stu-id="c0aae-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="c0aae-109">Une expression de requête LINQ pour une collection d’attributs a une apparence très semblable à une expression de requête LINQ pour une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="c0aae-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="c0aae-110">L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé.</span><span class="sxs-lookup"><span data-stu-id="c0aae-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="c0aae-111">Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="c0aae-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="c0aae-112">Le constructeur XAttribute</span><span class="sxs-lookup"><span data-stu-id="c0aae-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="c0aae-113">Le constructeur suivant de la classe <xref:System.Xml.Linq.XAttribute> est celui que vous utiliserez le plus souvent :</span><span class="sxs-lookup"><span data-stu-id="c0aae-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="c0aae-114">Constructeur</span><span class="sxs-lookup"><span data-stu-id="c0aae-114">Constructor</span></span>|<span data-ttu-id="c0aae-115">Description</span><span class="sxs-lookup"><span data-stu-id="c0aae-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="c0aae-116">Elle crée un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c0aae-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="c0aae-117">L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="c0aae-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="c0aae-118">Création d'un élément avec un attribut</span><span class="sxs-lookup"><span data-stu-id="c0aae-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="c0aae-119">Le code suivant illustre un élément qui contient un attribut à l’aide de littéraux XML dans Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="c0aae-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="c0aae-120">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c0aae-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="c0aae-121">Construction fonctionnelle d'attributs</span><span class="sxs-lookup"><span data-stu-id="c0aae-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="c0aae-122">Vous pouvez construire des objets <xref:System.Xml.Linq.XAttribute> en ligne avec la construction d'objets <xref:System.Xml.Linq.XElement> de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="c0aae-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="c0aae-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c0aae-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="c0aae-124">Les attributs ne sont pas des nœuds</span><span class="sxs-lookup"><span data-stu-id="c0aae-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="c0aae-125">Il existe certaines différences entre les attributs et les éléments.</span><span class="sxs-lookup"><span data-stu-id="c0aae-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="c0aae-126">Les objets <xref:System.Xml.Linq.XAttribute> ne sont pas des nœuds dans l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="c0aae-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="c0aae-127">Il s'agit de paires nom/valeur associées à un élément XML.</span><span class="sxs-lookup"><span data-stu-id="c0aae-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="c0aae-128">Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML.</span><span class="sxs-lookup"><span data-stu-id="c0aae-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="c0aae-129">Bien que les objets <xref:System.Xml.Linq.XAttribute> ne soient pas réellement des nœuds de l'arborescence XML, l'utilisation d'objets <xref:System.Xml.Linq.XAttribute> s'apparente à l'utilisation d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c0aae-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="c0aae-130">Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud.</span><span class="sxs-lookup"><span data-stu-id="c0aae-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="c0aae-131">De nombreux développeurs n'auront pas à se sourcier de cette distinction.</span><span class="sxs-lookup"><span data-stu-id="c0aae-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0aae-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0aae-132">See also</span></span>

- [<span data-ttu-id="c0aae-133">Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0aae-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
