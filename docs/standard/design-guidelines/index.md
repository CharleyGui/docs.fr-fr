---
title: Règles de conception de .NET Framework
description: Consultez les instructions de conception d’infrastructure pour la conception de bibliothèques qui étendent et interagissent avec .NET, pour garantir la cohérence et la facilité d’utilisation des API.
titleSuffix: ''
ms.date: 10/22/2008
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 9dc764492e1ac565c51d49d07e6566295bb76bc1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821032"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="1c5d7-103">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1c5d7-103">Framework Design Guidelines</span></span>
<span data-ttu-id="1c5d7-104">Cette section fournit des instructions pour concevoir des bibliothèques qui étendent et interagissent avec l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="1c5d7-105">L’objectif est d’aider les concepteurs de bibliothèques à garantir la cohérence et la facilité d’utilisation des API en fournissant un modèle de programmation unifié qui est indépendant du langage de programmation utilisé pour le développement.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="1c5d7-106">Nous vous recommandons de suivre ces instructions de conception lors du développement de classes et de composants qui étendent les .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="1c5d7-107">Une conception incohérente de la bibliothèque affecte la productivité des développeurs et déconseille l’adoption.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="1c5d7-108">Les instructions sont organisées en tant que recommandations simples précédées des termes `Do` ,, `Consider` `Avoid` et `Do not` .</span><span class="sxs-lookup"><span data-stu-id="1c5d7-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="1c5d7-109">Ces instructions sont destinées à aider les concepteurs de bibliothèques de classes à comprendre les compromis entre les différentes solutions.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="1c5d7-110">Il peut y avoir des situations où une bonne conception de bibliothèque exige que vous violiez ces règles de conception.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="1c5d7-111">Ce cas de figure doit être rare et il est important que vous ayez une raison claire et attrayante pour votre décision.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="1c5d7-112">Ces instructions sont extraites des règles de *conception de la structure Book : conventions, idiomes et modèles pour les bibliothèques .net réutilisables, 2e édition*, par Krzysztof Cwalina et Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c5d7-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1c5d7-113">In This Section</span></span>  
 [<span data-ttu-id="1c5d7-114">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="1c5d7-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="1c5d7-115">Fournit des instructions pour nommer les assemblys, les espaces de noms, les types et les membres dans les bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="1c5d7-116">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="1c5d7-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="1c5d7-117">Fournit des instructions pour l’utilisation des classes, des interfaces, des énumérations, des structures et des types statiques et abstraits.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="1c5d7-118">Recommandations en matière de conception de membres</span><span class="sxs-lookup"><span data-stu-id="1c5d7-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="1c5d7-119">Fournit des indications sur la conception et l’utilisation des propriétés, des méthodes, des constructeurs, des champs, des événements, des opérateurs et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="1c5d7-120">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="1c5d7-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="1c5d7-121">Traite des mécanismes d’extensibilité tels que le sous-classing, l’utilisation d’événements, de membres virtuels et de rappels, et explique comment choisir les mécanismes qui répondent le mieux aux besoins de votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="1c5d7-122">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="1c5d7-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="1c5d7-123">Décrit les instructions de conception pour la conception, la levée et l’interception des exceptions.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="1c5d7-124">Instructions d’utilisation</span><span class="sxs-lookup"><span data-stu-id="1c5d7-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="1c5d7-125">Fournit des instructions pour l’utilisation de types communs tels que des tableaux, des attributs et des collections, la prise en charge de la sérialisation et la surcharge des opérateurs d’égalité.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="1c5d7-126">Modèles de conception courants</span><span class="sxs-lookup"><span data-stu-id="1c5d7-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="1c5d7-127">Fournit des instructions pour le choix et l’implémentation des propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="1c5d7-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="1c5d7-128">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="1c5d7-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1c5d7-129">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1c5d7-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5d7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c5d7-130">See also</span></span>

- [<span data-ttu-id="1c5d7-131">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1c5d7-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="1c5d7-132">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="1c5d7-132">Development Guide</span></span>](../../framework/development-guide.md)
