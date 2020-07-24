---
title: Comment récupérer un seul attribut (LINQ to XML) (C#)
description: Découvrez comment utiliser LINQ to XML récupérer un attribut unique d’un élément en C#, étant donné le nom de l’attribut.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103437"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="d4c3e-103">Comment récupérer un seul attribut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4c3e-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d4c3e-104">Cette rubrique explique comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="d4c3e-105">Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="d4c3e-106">La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c3e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="d4c3e-107">Example</span></span>  
 <span data-ttu-id="d4c3e-108">L'exemple suivant utilise la méthode <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="d4c3e-109">Cet exemple recherche tous les descendants dans l'arborescence nommés `Phone`, puis recherche l'attribut nommé `type`.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="d4c3e-110">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d4c3e-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="d4c3e-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d4c3e-111">Example</span></span>  
 <span data-ttu-id="d4c3e-112">Si vous souhaitez récupérer la valeur de l'attribut vous pouvez le convertir, comme vous le feriez avec des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d4c3e-113">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-113">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="d4c3e-114">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d4c3e-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d4c3e-115">fournit des opérateurs de conversion explicites pour la classe <xref:System.Xml.Linq.XAttribute> vers `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c3e-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d4c3e-116">Example</span></span>  
 <span data-ttu-id="d4c3e-117">L'exemple suivant illustre le même code pour un attribut qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d4c3e-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="d4c3e-118">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d4c3e-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="d4c3e-119">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d4c3e-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4c3e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4c3e-120">See also</span></span>

- [<span data-ttu-id="d4c3e-121">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d4c3e-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
