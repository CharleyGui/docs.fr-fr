---
title: Conserver les paires nom-valeur-LINQ to XML
description: Découvrez comment utiliser LINQ to XML méthodes pour gérer un ensemble de paires nom-valeur.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553279"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a><span data-ttu-id="9fedb-103">Conserver les paires nom-valeur (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9fedb-103">Maintain name-value pairs (LINQ to XML)</span></span>

<span data-ttu-id="9fedb-104">De nombreuses applications doivent gérer des informations qui sont mieux conservées en tant que paires nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="9fedb-104">Many applications have to maintain information that is best kept as name-value pairs.</span></span> <span data-ttu-id="9fedb-105">Il peut s'agir d'informations de configuration ou de paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="9fedb-105">This information might be configuration information or global settings.</span></span> <span data-ttu-id="9fedb-106">LINQ to XML contient des méthodes qui facilitent la maintenance d’un ensemble de paires nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="9fedb-106">LINQ to XML contains methods that make it easy to maintain a set of name-value pairs.</span></span> <span data-ttu-id="9fedb-107">Vous pouvez conserver les informations en tant qu'attributs ou en tant qu'ensemble d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="9fedb-107">You can either keep the information as attributes or as a set of child elements.</span></span>

<span data-ttu-id="9fedb-108">L'une des différences est qu'il ne peut y avoir qu'un seul attribut avec un nom donné pour un élément.</span><span class="sxs-lookup"><span data-stu-id="9fedb-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="9fedb-109">Cette limitation ne s’applique pas aux éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="9fedb-109">This limitation doesn't apply to child elements.</span></span>

## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="9fedb-110">SetAttributeValue et SetElementValue</span><span class="sxs-lookup"><span data-stu-id="9fedb-110">SetAttributeValue and SetElementValue</span></span>

<span data-ttu-id="9fedb-111">Les deux méthodes qui facilitent la conservation des paires nom-valeur sont <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> et <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fedb-111">The two methods that facilitate keeping name-value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="9fedb-112">Ces deux méthodes ont une sémantique similaire.</span><span class="sxs-lookup"><span data-stu-id="9fedb-112">These two methods have similar semantics.</span></span>

<span data-ttu-id="9fedb-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> permet d’ajouter, de modifier et de supprimer des attributs d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9fedb-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, and remove attributes of an element.</span></span>

- <span data-ttu-id="9fedb-114">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d’un attribut qui n’existe pas, la méthode crée un nouvel attribut et l’ajoute à l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="9fedb-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that doesn't exist, the method creates a new attribute and adds it to the specified element.</span></span>
- <span data-ttu-id="9fedb-115">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut existant et avec du contenu spécifié, le contenu de l'attribut est remplacé par le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="9fedb-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>
- <span data-ttu-id="9fedb-116">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec le nom d’un attribut existant et que vous spécifiez `null` pour le contenu, l’attribut est supprimé de son parent.</span><span class="sxs-lookup"><span data-stu-id="9fedb-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify `null` for the content, the attribute is removed from its parent.</span></span>

<span data-ttu-id="9fedb-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> permet d’ajouter, de modifier et de supprimer des éléments enfants d’un élément.</span><span class="sxs-lookup"><span data-stu-id="9fedb-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, and remove child elements of an element.</span></span>

- <span data-ttu-id="9fedb-118">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d’un élément enfant qui n’existe pas, la méthode crée un nouvel élément et l’ajoute à l’élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="9fedb-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that doesn't exist, the method creates a new element and adds it to the specified element.</span></span>
- <span data-ttu-id="9fedb-119">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément existant et avec du contenu spécifié, le contenu de l'élément est remplacé par le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="9fedb-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>
- <span data-ttu-id="9fedb-120">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec le nom d’un élément existant et que vous spécifiez `null` pour le contenu, l’élément est supprimé de son parent.</span><span class="sxs-lookup"><span data-stu-id="9fedb-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify `null` for the content, the element is removed from its parent.</span></span>

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="9fedb-121">Exemple : utilisez `SetAttributeValue` pour créer et tenir à jour une liste de paires nom-valeur</span><span class="sxs-lookup"><span data-stu-id="9fedb-121">Example: Use `SetAttributeValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="9fedb-122">L'exemple suivant crée un élément sans attribut.</span><span class="sxs-lookup"><span data-stu-id="9fedb-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="9fedb-123">Il utilise ensuite la <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> méthode pour créer et gérer une liste de paires nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="9fedb-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="9fedb-124">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9fedb-124">This example produces the following output:</span></span>

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="9fedb-125">Exemple : utilisez `SetElementValue` pour créer et tenir à jour une liste de paires nom-valeur</span><span class="sxs-lookup"><span data-stu-id="9fedb-125">Example: Use `SetElementValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="9fedb-126">L'exemple suivant crée un élément sans élément enfant.</span><span class="sxs-lookup"><span data-stu-id="9fedb-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="9fedb-127">Il utilise ensuite la <xref:System.Xml.Linq.XElement.SetElementValue%2A> méthode pour créer et gérer une liste de paires nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="9fedb-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="9fedb-128">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9fedb-128">This example produces the following output:</span></span>

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="9fedb-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fedb-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
