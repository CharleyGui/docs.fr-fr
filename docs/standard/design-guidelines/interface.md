---
title: Conception d'interfaces
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 6f8cbb757ffb42f63903b212fee33cdcbba7ecb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727677"
---
# <a name="interface-design"></a><span data-ttu-id="fceed-102">Conception d'interfaces</span><span class="sxs-lookup"><span data-stu-id="fceed-102">Interface Design</span></span>

<span data-ttu-id="fceed-103">Bien que la plupart des API soient mieux modélisées à l’aide de classes et de structs, il existe des cas dans lesquels les interfaces sont plus appropriées ou sont la seule option.</span><span class="sxs-lookup"><span data-stu-id="fceed-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="fceed-104">Le CLR ne prend pas en charge l’héritage multiple (autrement dit, les classes CLR ne peuvent pas hériter de plusieurs classes de base), mais autorisent les types à implémenter une ou plusieurs interfaces en plus de l’héritage d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="fceed-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="fceed-105">Par conséquent, les interfaces sont souvent utilisées pour obtenir l’effet de plusieurs héritages.</span><span class="sxs-lookup"><span data-stu-id="fceed-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="fceed-106">Par exemple, <xref:System.IDisposable> est une interface qui permet aux types de prendre en charge disposability indépendamment de toute autre hiérarchie d’héritage dans laquelle ils souhaitent participer.</span><span class="sxs-lookup"><span data-stu-id="fceed-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="fceed-107">L’autre situation dans laquelle la définition d’une interface est appropriée est la création d’une interface commune qui peut être prise en charge par plusieurs types, y compris certains types valeur.</span><span class="sxs-lookup"><span data-stu-id="fceed-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="fceed-108">Les types valeur ne peuvent pas hériter de types autres que <xref:System.ValueType> , mais ils peuvent implémenter des interfaces. par conséquent, l’utilisation d’une interface est la seule option pour fournir un type de base commun.</span><span class="sxs-lookup"><span data-stu-id="fceed-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="fceed-109">✔️ définir une interface si vous avez besoin d’une API commune prise en charge par un ensemble de types incluant des types valeur.</span><span class="sxs-lookup"><span data-stu-id="fceed-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="fceed-110">✔️ envisagez de définir une interface si vous devez prendre en charge ses fonctionnalités sur les types qui héritent déjà d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="fceed-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="fceed-111">❌ Évitez d’utiliser des interfaces de marqueur (interfaces sans membres).</span><span class="sxs-lookup"><span data-stu-id="fceed-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="fceed-112">Si vous avez besoin de marquer une classe comme ayant une caractéristique spécifique (marqueur), en général, utilisez un attribut personnalisé plutôt qu’une interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="fceed-113">✔️ fournissez au moins un type qui est une implémentation d’une interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="fceed-114">Cela permet de valider la conception de l’interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="fceed-115">Par exemple, <xref:System.Collections.Generic.List%601> est une implémentation de l' <xref:System.Collections.Generic.IList%601> interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="fceed-116">✔️ fournissez au moins une API qui utilise chaque interface que vous définissez (une méthode qui prend l’interface en tant que paramètre ou une propriété de type interface).</span><span class="sxs-lookup"><span data-stu-id="fceed-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="fceed-117">Cela permet de valider la conception de l’interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="fceed-118">Par exemple, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> utilise l' <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="fceed-119">❌ N’ajoutez pas de membres à une interface qui a déjà été expédiée.</span><span class="sxs-lookup"><span data-stu-id="fceed-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="fceed-120">Cela entraînerait l’arrêt des implémentations de l’interface.</span><span class="sxs-lookup"><span data-stu-id="fceed-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="fceed-121">Vous devez créer une nouvelle interface afin d’éviter les problèmes de Versioning.</span><span class="sxs-lookup"><span data-stu-id="fceed-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="fceed-122">À l’exception des situations décrites dans ces instructions, vous devez, en général, choisir des classes plutôt que des interfaces pour concevoir des bibliothèques réutilisables de code managé.</span><span class="sxs-lookup"><span data-stu-id="fceed-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="fceed-123">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="fceed-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fceed-124">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fceed-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fceed-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fceed-125">See also</span></span>

- [<span data-ttu-id="fceed-126">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="fceed-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="fceed-127">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="fceed-127">Framework Design Guidelines</span></span>](index.md)
