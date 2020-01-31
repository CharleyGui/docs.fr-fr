---
title: Membres virtuels
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 8ed519a01162056151d8ae6398c0d06495911afd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743526"
---
# <a name="virtual-members"></a><span data-ttu-id="f0207-102">Membres virtuels</span><span class="sxs-lookup"><span data-stu-id="f0207-102">Virtual Members</span></span>
<span data-ttu-id="f0207-103">Les membres virtuels peuvent être remplacés, ce qui modifie le comportement de la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="f0207-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="f0207-104">Elles sont assez similaires aux rappels en termes d’extensibilité, mais elles sont préférables en termes de performances d’exécution et de consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f0207-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="f0207-105">En outre, les membres virtuels s’apaisent plus naturellement dans les scénarios qui requièrent la création d’un type spécial de type existant (spécialisation).</span><span class="sxs-lookup"><span data-stu-id="f0207-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="f0207-106">Les membres virtuels sont plus performants que les rappels et les événements, mais ne sont pas plus performants que les méthodes non virtuelles.</span><span class="sxs-lookup"><span data-stu-id="f0207-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="f0207-107">Le principal inconvénient des membres virtuels est que le comportement d’un membre virtuel ne peut être modifié qu’au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f0207-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="f0207-108">Le comportement d’un rappel peut être modifié au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0207-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="f0207-109">Les membres virtuels, comme les rappels (et peut-être plus que les rappels), sont coûteux pour la conception, le test et la maintenance, car tout appel à un membre virtuel peut être substitué de manière imprévisible et peut exécuter du code arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f0207-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="f0207-110">En outre, un plus grand nombre d’efforts est généralement requis pour définir clairement le contrat des membres virtuels, de sorte que le coût de la conception et de la documentation est plus élevé.</span><span class="sxs-lookup"><span data-stu-id="f0207-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="f0207-111">❌ ne faites pas de membres virtuels, sauf si vous avez une bonne raison de le faire et que vous connaissez tous les coûts liés à la conception, au test et à la maintenance des membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="f0207-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="f0207-112">Les membres virtuels sont moins indulgent avec en termes de modifications qui peuvent être apportées sans interrompre la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="f0207-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="f0207-113">En outre, ils sont plus lents que les membres non virtuels, principalement parce que les appels aux membres virtuels ne sont pas Inline.</span><span class="sxs-lookup"><span data-stu-id="f0207-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="f0207-114">✔️ ENVISAGER de limiter l’extensibilité à ce qui est absolument nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f0207-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="f0207-115">✔️ préférez l’accessibilité protégée par rapport à l’accessibilité publique pour les membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="f0207-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="f0207-116">Les membres publics doivent fournir une extensibilité (si nécessaire) en appelant dans un membre virtuel protégé.</span><span class="sxs-lookup"><span data-stu-id="f0207-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="f0207-117">Les membres publics d’une classe doivent fournir le jeu de fonctionnalités approprié aux consommateurs directs de cette classe.</span><span class="sxs-lookup"><span data-stu-id="f0207-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="f0207-118">Les membres virtuels sont conçus pour être remplacés dans les sous-classes et l’accessibilité protégée est un excellent moyen d’étendre l’ensemble des points d’extensibilité virtuels à l’emplacement où ils peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="f0207-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="f0207-119">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="f0207-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f0207-120">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f0207-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f0207-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0207-121">See also</span></span>

- [<span data-ttu-id="f0207-122">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f0207-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f0207-123">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="f0207-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
