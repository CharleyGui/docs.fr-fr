---
title: Instructions d'attribution de noms
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
ms.openlocfilehash: ad98c0f3b02bdc81e6348493b4e0a02f9cb20ed4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709190"
---
# <a name="naming-guidelines"></a><span data-ttu-id="a1f83-102">Instructions d'attribution de noms</span><span class="sxs-lookup"><span data-stu-id="a1f83-102">Naming Guidelines</span></span>
<span data-ttu-id="a1f83-103">À la suite d’un ensemble cohérent de conventions d’affectation de noms dans le développement d’une infrastructure, il peut s’agir d’une contribution majeure à la facilité d’utilisation du Framework.</span><span class="sxs-lookup"><span data-stu-id="a1f83-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="a1f83-104">Il permet à un grand nombre de développeurs d’utiliser le Framework sur des projets largement séparés.</span><span class="sxs-lookup"><span data-stu-id="a1f83-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="a1f83-105">Au-delà de la cohérence de la forme, les noms des éléments de l’infrastructure doivent être facilement compris et doivent communiquer avec la fonction de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="a1f83-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="a1f83-106">L’objectif de ce chapitre est de fournir un ensemble cohérent de conventions d’affectation de noms qui se traduit par des noms qui prennent un sens immédiat pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="a1f83-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="a1f83-107">Bien que l’adoption de ces conventions d’affectation de noms en tant que directives de développement de code générales produirait des noms plus cohérents dans votre code, vous ne devez les appliquer qu’aux API qui sont exposées publiquement (types et membres publics ou protégés, et interfaces implémentées explicitement).</span><span class="sxs-lookup"><span data-stu-id="a1f83-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1f83-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a1f83-108">In This Section</span></span>  
 [<span data-ttu-id="a1f83-109">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="a1f83-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="a1f83-110">Conventions générales de nommage</span><span class="sxs-lookup"><span data-stu-id="a1f83-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="a1f83-111">Noms d’assemblys et de DLL</span><span class="sxs-lookup"><span data-stu-id="a1f83-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="a1f83-112">Noms d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="a1f83-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="a1f83-113">Noms de classes, de structures et d’interfaces</span><span class="sxs-lookup"><span data-stu-id="a1f83-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="a1f83-114">Noms de membres de type</span><span class="sxs-lookup"><span data-stu-id="a1f83-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="a1f83-115">Nommage des paramètres</span><span class="sxs-lookup"><span data-stu-id="a1f83-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="a1f83-116">Nommage des ressources</span><span class="sxs-lookup"><span data-stu-id="a1f83-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="a1f83-117">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="a1f83-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a1f83-118">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a1f83-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f83-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1f83-119">See also</span></span>

- [<span data-ttu-id="a1f83-120">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1f83-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
