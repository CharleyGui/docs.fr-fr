---
title: Accès à du code XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351746"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="ed3b6-102">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed3b6-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="ed3b6-103">Visual Basic fournit des propriétés d’axe XML pour accéder aux structures [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] et les parcourir.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="ed3b6-104">Ces propriétés utilisent une syntaxe spéciale pour vous permettre d’accéder aux éléments et aux attributs en spécifiant les noms XML.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="ed3b6-105">Le tableau suivant répertorie les fonctionnalités de langage qui vous permettent d’accéder aux éléments et attributs XML dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="ed3b6-106">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="ed3b6-107">Description de la propriété</span><span class="sxs-lookup"><span data-stu-id="ed3b6-107">Property description</span></span>|<span data-ttu-id="ed3b6-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed3b6-108">Example</span></span>|<span data-ttu-id="ed3b6-109">Description</span><span class="sxs-lookup"><span data-stu-id="ed3b6-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="ed3b6-110">*axe enfant*</span><span class="sxs-lookup"><span data-stu-id="ed3b6-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="ed3b6-111">Obtient tous les éléments `phone` qui sont des éléments enfants de l’élément `contact`.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="ed3b6-112">*axe d’attribut*</span><span class="sxs-lookup"><span data-stu-id="ed3b6-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="ed3b6-113">Obtient tous les attributs `type` de l’élément `phone`.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="ed3b6-114">*axe descendant*</span><span class="sxs-lookup"><span data-stu-id="ed3b6-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="ed3b6-115">Obtient tous les éléments `name` de l’élément `contacts`, quelle que soit la profondeur de la hiérarchie à laquelle ils se produisent.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="ed3b6-116">*indexeur d’extension*</span><span class="sxs-lookup"><span data-stu-id="ed3b6-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="ed3b6-117">Obtient le premier élément `name` de la séquence.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="ed3b6-118">*valeur*</span><span class="sxs-lookup"><span data-stu-id="ed3b6-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="ed3b6-119">Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="ed3b6-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ed3b6-120">In This Section</span></span>  
 [<span data-ttu-id="ed3b6-121">Guide pratique : accéder à des éléments descendants XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="ed3b6-122">Montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML spécifié.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="ed3b6-123">Guide pratique : accéder à des éléments enfants XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="ed3b6-124">Montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="ed3b6-125">Guide pratique : accéder à des attributs XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="ed3b6-126">Montre comment utiliser une propriété d’axe d’attribut pour accéder à tous les attributs XML portant un nom spécifié dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="ed3b6-127">Guide pratique : déclarer et utiliser des préfixes d’espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="ed3b6-128">Montre comment déclarer un préfixe d’espace de noms XML et l’utiliser pour créer des éléments XML et y accéder.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ed3b6-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="ed3b6-129">Related Sections</span></span>  
 [<span data-ttu-id="ed3b6-130">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="ed3b6-131">Fournit des liens vers des sections décrivant les différentes propriétés d’accès XML.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="ed3b6-132">Vue d’ensemble de LINQ to XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed3b6-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="ed3b6-133">Fournit une introduction à l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ed3b6-134">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed3b6-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="ed3b6-135">Fournit une introduction à l’utilisation de littéraux XML dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ed3b6-136">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed3b6-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="ed3b6-137">Fournit des liens vers des sections relatives au chargement et à la modification de code XML dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ed3b6-138">XML</span><span class="sxs-lookup"><span data-stu-id="ed3b6-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="ed3b6-139">Fournit des liens vers des sections décrivant l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed3b6-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
