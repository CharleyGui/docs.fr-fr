---
title: Règles de maintenabilité (analyse du code)
description: En savoir plus sur les règles de maintenabilité de l’analyse du code.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586960"
---
# <a name="maintainability-rules"></a><span data-ttu-id="07923-103">Règles de maintenabilité</span><span class="sxs-lookup"><span data-stu-id="07923-103">Maintainability rules</span></span>

<span data-ttu-id="07923-104">Les règles de maintenabilité prennent en charge la gestion des bibliothèques et des applications.</span><span class="sxs-lookup"><span data-stu-id="07923-104">Maintainability rules support library and application maintenance.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="07923-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="07923-105">In this section</span></span>

| <span data-ttu-id="07923-106">Règle</span><span class="sxs-lookup"><span data-stu-id="07923-106">Rule</span></span> | <span data-ttu-id="07923-107">Description</span><span class="sxs-lookup"><span data-stu-id="07923-107">Description</span></span> |
|-----------|-----------------------------------|
| [<span data-ttu-id="07923-108">CA1501 : Éviter l'excès d'héritage</span><span class="sxs-lookup"><span data-stu-id="07923-108">CA1501: Avoid excessive inheritance</span></span>](ca1501.md) | <span data-ttu-id="07923-109">Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage.</span><span class="sxs-lookup"><span data-stu-id="07923-109">A type is more than four levels deep in its inheritance hierarchy.</span></span> <span data-ttu-id="07923-110">Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer.</span><span class="sxs-lookup"><span data-stu-id="07923-110">Deeply nested type hierarchies can be difficult to follow, understand, and maintain.</span></span> |
| [<span data-ttu-id="07923-111">CA1502 : Éviter l'excès de complexité</span><span class="sxs-lookup"><span data-stu-id="07923-111">CA1502: Avoid excessive complexity</span></span>](ca1502.md) | <span data-ttu-id="07923-112">Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="07923-112">This rule measures the number of linearly independent paths through the method, which is determined by the number and complexity of conditional branches.</span></span> |
| [<span data-ttu-id="07923-113">CA1505 : Éviter le code impossible à maintenir</span><span class="sxs-lookup"><span data-stu-id="07923-113">CA1505: Avoid unmaintainable code</span></span>](ca1505.md) | <span data-ttu-id="07923-114">Un type ou une méthode a une faible valeur d'indice de maintenabilité.</span><span class="sxs-lookup"><span data-stu-id="07923-114">A type or method has a low maintainability index value.</span></span> <span data-ttu-id="07923-115">Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception.</span><span class="sxs-lookup"><span data-stu-id="07923-115">A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate for redesign.</span></span> |
| [<span data-ttu-id="07923-116">CA1506 : Éviter les couplages de classe excessifs</span><span class="sxs-lookup"><span data-stu-id="07923-116">CA1506: Avoid excessive class coupling</span></span>](ca1506.md) | <span data-ttu-id="07923-117">Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="07923-117">This rule measures class coupling by counting the number of unique type references that a type or method contains.</span></span> |
| [<span data-ttu-id="07923-118">CA1507 : Utiliser nameof à la place de string</span><span class="sxs-lookup"><span data-stu-id="07923-118">CA1507: Use nameof in place of string</span></span>](ca1507.md) | <span data-ttu-id="07923-119">Un littéral de chaîne est utilisé en tant qu’argument dans lequel une `nameof` expression peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="07923-119">A string literal is used as an argument where a `nameof` expression could be used.</span></span> |
| [<span data-ttu-id="07923-120">CA1508 : Éviter le code conditionnel mort</span><span class="sxs-lookup"><span data-stu-id="07923-120">CA1508: Avoid dead conditional code</span></span>](ca1508.md) | <span data-ttu-id="07923-121">Une méthode a un code conditionnel qui prend toujours la valeur `true` ou `false` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="07923-121">A method has conditional code that always evaluates to `true` or `false` at runtime.</span></span> <span data-ttu-id="07923-122">Cela provoque un code mort dans la `false` branche de la condition.</span><span class="sxs-lookup"><span data-stu-id="07923-122">This leads to dead code in the `false` branch of the condition.</span></span> |
| [<span data-ttu-id="07923-123">CA1509 : Entrée non valide dans le fichier de configuration des métriques de code</span><span class="sxs-lookup"><span data-stu-id="07923-123">CA1509: Invalid entry in code metrics configuration file</span></span>](ca1509.md) | <span data-ttu-id="07923-124">Les règles de métrique du code, telles que [CA1501](ca1501.md), [CA1502](ca1502.md), [ca1505](ca1505.md) et [CA1506](ca1506.md), ont fourni un fichier de configuration nommé `CodeMetricsConfig.txt` qui a une entrée non valide.</span><span class="sxs-lookup"><span data-stu-id="07923-124">Code metrics rules, such as [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) and [CA1506](ca1506.md), supplied a configuration file named `CodeMetricsConfig.txt` that has an invalid entry.</span></span> |

## <a name="see-also"></a><span data-ttu-id="07923-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07923-125">See also</span></span>

- [<span data-ttu-id="07923-126">Mesure de la complexité et de la facilité de maintenance du code managé</span><span class="sxs-lookup"><span data-stu-id="07923-126">Measure Complexity and Maintainability of Managed Code</span></span>](/visualstudio/code-quality/code-metrics-values)
