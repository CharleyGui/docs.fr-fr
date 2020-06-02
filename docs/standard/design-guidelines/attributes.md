---
title: Attributs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280580"
---
# <a name="attributes"></a><span data-ttu-id="74f89-102">Attributs</span><span class="sxs-lookup"><span data-stu-id="74f89-102">Attributes</span></span>

<span data-ttu-id="74f89-103"><xref:System.Attribute?displayProperty=nameWithType>est une classe de base utilisée pour définir des attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="74f89-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="74f89-104">Les attributs sont des annotations qui peuvent être ajoutées aux éléments de programmation tels que les assemblys, les types, les membres et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="74f89-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="74f89-105">Elles sont stockées dans les métadonnées de l’assembly et sont accessibles au moment de l’exécution à l’aide des API de réflexion.</span><span class="sxs-lookup"><span data-stu-id="74f89-105">They are stored in the metadata of the assembly and can be accessed at run time using the reflection APIs.</span></span> <span data-ttu-id="74f89-106">Par exemple, .NET définit l' <xref:System.ObsoleteAttribute> attribut, qui peut être appliqué à un type ou un membre pour indiquer que le type ou le membre a été déconseillé.</span><span class="sxs-lookup"><span data-stu-id="74f89-106">For example, .NET defines the <xref:System.ObsoleteAttribute> attribute, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="74f89-107">Les attributs peuvent avoir une ou plusieurs propriétés qui contiennent des données supplémentaires relatives à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="74f89-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="74f89-108">Par exemple, `ObsoleteAttribute` peut contenir des informations supplémentaires sur la version dans laquelle un type ou un membre a été déconseillé et une description de la nouvelle API qui remplace l’API obsolète.</span><span class="sxs-lookup"><span data-stu-id="74f89-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and a description of the new API that replaces the obsolete API.</span></span>

 <span data-ttu-id="74f89-109">Certaines propriétés d’un attribut doivent être spécifiées quand l’attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="74f89-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="74f89-110">Ils sont appelés propriétés requises ou arguments requis, car ils sont représentés en tant que paramètres de constructeur positionnel.</span><span class="sxs-lookup"><span data-stu-id="74f89-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="74f89-111">Par exemple, la <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriété de <xref:System.Diagnostics.ConditionalAttribute> est une propriété obligatoire.</span><span class="sxs-lookup"><span data-stu-id="74f89-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="74f89-112">Les propriétés qui n’ont pas nécessairement besoin d’être spécifiées lors de l’application de l’attribut sont appelées propriétés facultatives (ou arguments facultatifs).</span><span class="sxs-lookup"><span data-stu-id="74f89-112">Properties that don't necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="74f89-113">Elles sont représentées par des propriétés définissables.</span><span class="sxs-lookup"><span data-stu-id="74f89-113">They are represented by settable properties.</span></span> <span data-ttu-id="74f89-114">Les compilateurs fournissent une syntaxe spéciale pour définir ces propriétés lorsqu’un attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="74f89-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="74f89-115">Par exemple, la <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriété représente un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="74f89-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="74f89-116">✔️ Nommez les classes d’attributs personnalisés avec le suffixe « Attribute ».</span><span class="sxs-lookup"><span data-stu-id="74f89-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="74f89-117">✔️ appliquez à des <xref:System.AttributeUsageAttribute> attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="74f89-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="74f89-118">✔️ fournissez des propriétés définissables pour les arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="74f89-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="74f89-119">✔️ fournissez des propriétés d’extraction uniquement pour les arguments requis.</span><span class="sxs-lookup"><span data-stu-id="74f89-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="74f89-120">✔️ fournissez des paramètres de constructeur pour initialiser les propriétés correspondant aux arguments requis.</span><span class="sxs-lookup"><span data-stu-id="74f89-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="74f89-121">Chaque paramètre doit avoir le même nom (mais avec une casse différente) que la propriété correspondante.</span><span class="sxs-lookup"><span data-stu-id="74f89-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="74f89-122">❌Évitez de fournir des paramètres de constructeur pour initialiser les propriétés correspondant aux arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="74f89-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="74f89-123">En d’autres termes, les propriétés ne peuvent pas être définies avec un constructeur et un accesseur Set.</span><span class="sxs-lookup"><span data-stu-id="74f89-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="74f89-124">Cette recommandation rend très explicite les arguments facultatifs et obligatoires, et évite d’avoir deux façons de faire la même chose.</span><span class="sxs-lookup"><span data-stu-id="74f89-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="74f89-125">❌Évitez de surcharger les constructeurs d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="74f89-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="74f89-126">Le fait de n’avoir qu’un seul constructeur communique clairement à l’utilisateur les arguments requis et ceux qui sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="74f89-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="74f89-127">✔️ scellent les classes d’attributs personnalisés, si possible.</span><span class="sxs-lookup"><span data-stu-id="74f89-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="74f89-128">La recherche de l’attribut est ainsi plus rapide.</span><span class="sxs-lookup"><span data-stu-id="74f89-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="74f89-129">*Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="74f89-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="74f89-130">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="74f89-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="74f89-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74f89-131">See also</span></span>

- [<span data-ttu-id="74f89-132">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="74f89-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="74f89-133">Instructions d’utilisation</span><span class="sxs-lookup"><span data-stu-id="74f89-133">Usage Guidelines</span></span>](usage-guidelines.md)
