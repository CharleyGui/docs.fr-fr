---
title: Sceller
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: ddf463e98fb6a9c5ccaae90e9cfc74b5691b13a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743627"
---
# <a name="sealing"></a><span data-ttu-id="73a9e-102">Sceller</span><span class="sxs-lookup"><span data-stu-id="73a9e-102">Sealing</span></span>
<span data-ttu-id="73a9e-103">L’une des fonctionnalités des frameworks orientés objet est que les développeurs peuvent les étendre et les personnaliser de manière inattendue par les concepteurs de Framework.</span><span class="sxs-lookup"><span data-stu-id="73a9e-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="73a9e-104">Il s’agit de la puissance et du danger de la conception extensible.</span><span class="sxs-lookup"><span data-stu-id="73a9e-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="73a9e-105">Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement l’extensibilité quand vous le souhaitez, et de limiter l’extensibilité quand elle est dangereuse.</span><span class="sxs-lookup"><span data-stu-id="73a9e-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="73a9e-106">Mécanisme puissant qui empêche la fermeture de l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="73a9e-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="73a9e-107">Vous pouvez sceller la classe ou des membres individuels.</span><span class="sxs-lookup"><span data-stu-id="73a9e-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="73a9e-108">La fermeture d’une classe empêche les utilisateurs d’hériter de la classe.</span><span class="sxs-lookup"><span data-stu-id="73a9e-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="73a9e-109">La fermeture d’un membre empêche les utilisateurs de se substituer à un membre particulier.</span><span class="sxs-lookup"><span data-stu-id="73a9e-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="73a9e-110">❌ ne scellez pas les classes sans avoir une bonne raison de le faire.</span><span class="sxs-lookup"><span data-stu-id="73a9e-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="73a9e-111">Sceller une classe parce que vous ne pouvez pas considérer un scénario d’extensibilité n’est pas une bonne raison.</span><span class="sxs-lookup"><span data-stu-id="73a9e-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="73a9e-112">Les utilisateurs de l’infrastructure aiment hériter des classes pour différentes raisons qui ne sont pas évidentes, comme l’ajout de membres de commodité.</span><span class="sxs-lookup"><span data-stu-id="73a9e-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="73a9e-113">Consultez [classes non scellées](../../../docs/standard/design-guidelines/unsealed-classes.md) pour obtenir des exemples de raisons non évidentes que les utilisateurs souhaitent hériter d’un type.</span><span class="sxs-lookup"><span data-stu-id="73a9e-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="73a9e-114">Les bonnes raisons pour sceller une classe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="73a9e-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="73a9e-115">La classe est une classe statique.</span><span class="sxs-lookup"><span data-stu-id="73a9e-115">The class is a static class.</span></span> <span data-ttu-id="73a9e-116">Consultez [conception de classes statiques](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="73a9e-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>

- <span data-ttu-id="73a9e-117">La classe stocke des secrets sensibles à la sécurité dans les membres protégés hérités.</span><span class="sxs-lookup"><span data-stu-id="73a9e-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="73a9e-118">La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement compenserait les avantages de laisser la classe non scellée.</span><span class="sxs-lookup"><span data-stu-id="73a9e-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="73a9e-119">La classe est un attribut qui nécessite une recherche très rapide au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="73a9e-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="73a9e-120">Les attributs scellés ont des niveaux de performances légèrement supérieurs à ceux des attributs non scellés.</span><span class="sxs-lookup"><span data-stu-id="73a9e-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="73a9e-121">Consultez [attributs](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="73a9e-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>

 <span data-ttu-id="73a9e-122">❌ ne déclarez pas de membres protégés ou virtuels sur les types sealed.</span><span class="sxs-lookup"><span data-stu-id="73a9e-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="73a9e-123">Par définition, les types sealed ne peuvent pas être hérités de.</span><span class="sxs-lookup"><span data-stu-id="73a9e-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="73a9e-124">Cela signifie que les membres protégés sur les types sealed ne peuvent pas être appelés, et les méthodes virtuelles sur les types sealed ne peuvent pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="73a9e-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="73a9e-125">✔️ envisagez de sceller les membres que vous substituez.</span><span class="sxs-lookup"><span data-stu-id="73a9e-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="73a9e-126">Les problèmes qui peuvent résulter de l’introduction de membres virtuels (décrits dans [membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)) s’appliquent également aux remplacements, bien qu’à un degré légèrement moindre.</span><span class="sxs-lookup"><span data-stu-id="73a9e-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="73a9e-127">Le scellage d’un remplacement vous protège de ces problèmes à partir de ce point dans la hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="73a9e-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="73a9e-128">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="73a9e-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="73a9e-129">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="73a9e-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="73a9e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73a9e-130">See also</span></span>

- [<span data-ttu-id="73a9e-131">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="73a9e-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="73a9e-132">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="73a9e-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="73a9e-133">Classes unsealed</span><span class="sxs-lookup"><span data-stu-id="73a9e-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
