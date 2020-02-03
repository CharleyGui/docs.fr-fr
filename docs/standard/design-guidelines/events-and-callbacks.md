---
title: Événements et rappels
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 7dab759ba48104530fc41e46f6f2bba18d6c4456
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741659"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="5e6bc-102">Événements et rappels</span><span class="sxs-lookup"><span data-stu-id="5e6bc-102">Events and Callbacks</span></span>
<span data-ttu-id="5e6bc-103">Les rappels sont des points d’extensibilité qui permettent à un Framework d’effectuer un rappel dans le code utilisateur via un délégué.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="5e6bc-104">Ces délégués sont généralement passés à l’infrastructure par le biais d’un paramètre d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="5e6bc-105">Les événements sont un cas spécial de rappels qui prend en charge une syntaxe pratique et cohérente pour fournir le délégué (un gestionnaire d’événements).</span><span class="sxs-lookup"><span data-stu-id="5e6bc-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="5e6bc-106">En outre, la saisie semi-automatique des instructions de Visual Studio et les concepteurs fournissent de l’aide pour l’utilisation des API basées sur les événements.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="5e6bc-107">(Voir [conception des événements](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="5e6bc-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>

 <span data-ttu-id="5e6bc-108">✔️ envisagez d’utiliser des rappels pour permettre aux utilisateurs de fournir un code personnalisé à exécuter par le Framework.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="5e6bc-109">✔️ envisagez d’utiliser des événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans avoir besoin de comprendre la conception orientée objet.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="5e6bc-110">✔️ préférez des événements aux rappels simples, car ils sont plus familiers à un plus grand nombre de développeurs et sont intégrés à la saisie semi-automatique des instructions Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="5e6bc-111">❌ Évitez d’utiliser des rappels dans les API sensibles aux performances.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="5e6bc-112">✔️ Utilisez les nouveaux types `Func<...>`, `Action<...>`ou `Expression<...>` au lieu des délégués personnalisés, lors de la définition d’API avec des rappels.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="5e6bc-113">`Func<...>` et `Action<...>` représentent des délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="5e6bc-114">`Expression<...>` représente des définitions de fonction qui peuvent être compilées et appelées par la suite au moment de l’exécution, mais qui peuvent également être sérialisées et passées à des processus distants.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="5e6bc-115">✔️ Mesurez et comprenez les implications en matière de performances de l’utilisation de `Expression<...>`, au lieu d’utiliser des délégués `Func<...>` et `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="5e6bc-116">les types de `Expression<...>` sont dans la plupart des cas logiquement équivalents aux délégués `Func<...>` et `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="5e6bc-117">La principale différence réside dans le fait que les délégués sont destinés à être utilisés dans les scénarios de processus local. les expressions sont prévues dans les cas où il est bénéfique et possible d’évaluer l’expression dans un processus ou un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="5e6bc-118">✔️ comprenez qu’en appelant un délégué, vous exécutez du code arbitraire et cela peut avoir des répercussions en matière de sécurité, d’exactitude et de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="5e6bc-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="5e6bc-119">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="5e6bc-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5e6bc-120">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5e6bc-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5e6bc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e6bc-121">See also</span></span>

- [<span data-ttu-id="5e6bc-122">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="5e6bc-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="5e6bc-123">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e6bc-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
