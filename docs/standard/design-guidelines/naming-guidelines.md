---
title: Indications concernant l'attribution d'un nom
description: Dans cette vue d’ensemble, consultez la page relative aux conventions d’affectation de noms à utiliser dans le développement de Framework. Accédez à des articles couvrant les majuscules, les noms généraux et d’autres instructions.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: fbcf5ef5eb02a5e45b5c981b4247ffe1c9c2631b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447145"
---
# <a name="naming-guidelines"></a><span data-ttu-id="a61fd-104">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="a61fd-104">Naming Guidelines</span></span>
<span data-ttu-id="a61fd-105">À la suite d’un ensemble cohérent de conventions d’affectation de noms dans le développement d’une infrastructure, il peut s’agir d’une contribution majeure à la facilité d’utilisation du Framework.</span><span class="sxs-lookup"><span data-stu-id="a61fd-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="a61fd-106">Il permet à un grand nombre de développeurs d’utiliser le Framework sur des projets largement séparés.</span><span class="sxs-lookup"><span data-stu-id="a61fd-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="a61fd-107">Au-delà de la cohérence de la forme, les noms des éléments de l’infrastructure doivent être facilement compris et doivent communiquer avec la fonction de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="a61fd-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="a61fd-108">L’objectif de ce chapitre est de fournir un ensemble cohérent de conventions d’affectation de noms qui se traduit par des noms qui prennent un sens immédiat pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="a61fd-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="a61fd-109">Bien que l’adoption de ces conventions d’affectation de noms en tant que directives de développement de code générales produirait des noms plus cohérents dans votre code, vous ne devez les appliquer qu’aux API qui sont exposées publiquement (types et membres publics ou protégés, et interfaces implémentées explicitement).</span><span class="sxs-lookup"><span data-stu-id="a61fd-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a61fd-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a61fd-110">In This Section</span></span>  
 [<span data-ttu-id="a61fd-111">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="a61fd-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="a61fd-112">Conventions d’affectation de noms générales</span><span class="sxs-lookup"><span data-stu-id="a61fd-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="a61fd-113">Noms d’assemblys et de dll</span><span class="sxs-lookup"><span data-stu-id="a61fd-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="a61fd-114">Noms des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="a61fd-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="a61fd-115">Noms de classes, de structures et d’interfaces</span><span class="sxs-lookup"><span data-stu-id="a61fd-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="a61fd-116">Noms des membres de type</span><span class="sxs-lookup"><span data-stu-id="a61fd-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="a61fd-117">Paramètres d’attribution de noms</span><span class="sxs-lookup"><span data-stu-id="a61fd-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="a61fd-118">Attribution de noms aux ressources</span><span class="sxs-lookup"><span data-stu-id="a61fd-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="a61fd-119">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="a61fd-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a61fd-120">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a61fd-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61fd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a61fd-121">See also</span></span>

- [<span data-ttu-id="a61fd-122">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="a61fd-122">Framework Design Guidelines</span></span>](index.md)
