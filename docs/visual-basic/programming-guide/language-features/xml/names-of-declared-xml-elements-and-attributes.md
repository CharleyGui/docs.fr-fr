---
title: Nom des attributs et des éléments XML déclarés
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2142674c3de4c5ac9e806c1328daa3efb697beb9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085618"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="91f1d-102">Nom des attributs et des éléments XML déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91f1d-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>

<span data-ttu-id="91f1d-103">Cette rubrique fournit des instructions Visual Basic pour nommer des éléments et des attributs XML dans des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="91f1d-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="91f1d-104">Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié.</span><span class="sxs-lookup"><span data-stu-id="91f1d-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="91f1d-105">Un nom qualifié se compose d’un préfixe d’espace de noms XML, d’un signe deux-points et d’un nom local.</span><span class="sxs-lookup"><span data-stu-id="91f1d-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="91f1d-106">Pour plus d’informations sur les préfixes d’espaces de noms XML, consultez [littéral d’élément XML](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="91f1d-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="91f1d-107">Règles</span><span class="sxs-lookup"><span data-stu-id="91f1d-107">Rules</span></span>  

 <span data-ttu-id="91f1d-108">Un nom local d’un élément ou d’un attribut dans Visual Basic doit respecter les règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="91f1d-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="91f1d-109">Il peut commencer par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="91f1d-109">It can begin with a namespace.</span></span> <span data-ttu-id="91f1d-110">Elle doit commencer par un caractère alphabétique ou un trait de soulignement ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="91f1d-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="91f1d-111">Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, des points (.) et des traits d’Union (-).</span><span class="sxs-lookup"><span data-stu-id="91f1d-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="91f1d-112">Sa longueur ne doit pas dépasser 1 024 caractères.</span><span class="sxs-lookup"><span data-stu-id="91f1d-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="91f1d-113">Les signes deux-points qui apparaissent dans les noms indiquent la délimitation de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="91f1d-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="91f1d-114">Par conséquent, vous ne pouvez utiliser les deux-points que pour spécifier un espace de noms XML pour un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="91f1d-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="91f1d-115">En outre, vous devez respecter les indications ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="91f1d-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="91f1d-116">La spécification XML 1,0 réserve tous les noms commençant par la chaîne « XML », quelle que soit la variation de la casse.</span><span class="sxs-lookup"><span data-stu-id="91f1d-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="91f1d-117">Par conséquent, n’utilisez pas ces noms pour les noms d’élément et d’attribut.</span><span class="sxs-lookup"><span data-stu-id="91f1d-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="91f1d-118">Instructions relatives à la longueur de nom</span><span class="sxs-lookup"><span data-stu-id="91f1d-118">Name Length Guidelines</span></span>  

 <span data-ttu-id="91f1d-119">En pratique, un nom doit être aussi bref que possible tout en identifiant clairement la nature de l’élément.</span><span class="sxs-lookup"><span data-stu-id="91f1d-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="91f1d-120">Cela permet d’améliorer la lisibilité de votre code et de réduire la longueur de ligne et la taille du fichier source.</span><span class="sxs-lookup"><span data-stu-id="91f1d-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="91f1d-121">Toutefois, votre nom ne doit pas être tellement bref qu’il ne décrit pas correctement l’élément ou la manière dont votre code l’utilise.</span><span class="sxs-lookup"><span data-stu-id="91f1d-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="91f1d-122">Cela est important pour la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="91f1d-122">This is important for the readability of your code.</span></span> <span data-ttu-id="91f1d-123">Si quelqu’un d’autre essaie de le comprendre ou si vous en examinez un certain temps après l’avoir écrit, les noms d’éléments appropriés peuvent vous faire gagner du temps.</span><span class="sxs-lookup"><span data-stu-id="91f1d-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="91f1d-124">Respect de la casse dans les noms</span><span class="sxs-lookup"><span data-stu-id="91f1d-124">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="91f1d-125">Les noms d’éléments XML respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="91f1d-125">XML element names are case sensitive.</span></span> <span data-ttu-id="91f1d-126">Cela signifie que lorsque le compilateur Visual Basic compare deux noms qui diffèrent uniquement par la casse alphabétique, il les interprète comme des noms différents.</span><span class="sxs-lookup"><span data-stu-id="91f1d-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="91f1d-127">Par exemple, il interprète `ABC` et `abc` comme faisant référence à des éléments distincts.</span><span class="sxs-lookup"><span data-stu-id="91f1d-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="91f1d-128">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="91f1d-128">XML Namespaces</span></span>  

 <span data-ttu-id="91f1d-129">Lorsque vous créez un littéral d’élément XML, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom d’élément.</span><span class="sxs-lookup"><span data-stu-id="91f1d-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="91f1d-130">Pour plus d’informations, consultez [littéral d’élément XML](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="91f1d-130">For more information, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f1d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91f1d-131">See also</span></span>

- [<span data-ttu-id="91f1d-132">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91f1d-132">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="91f1d-133">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="91f1d-133">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
