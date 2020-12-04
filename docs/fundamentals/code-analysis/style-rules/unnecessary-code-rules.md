---
title: Règles de code inutiles
description: En savoir plus sur les règles de code inutiles de l’analyse du code
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "96588413"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="8aac3-103">Règles de code inutiles</span><span class="sxs-lookup"><span data-stu-id="8aac3-103">Unnecessary code rules</span></span>

<span data-ttu-id="8aac3-104">Les règles de code inutiles identifient des parties différentes de la base de code qui ne sont pas nécessaires et peuvent être refactorées ou supprimées.</span><span class="sxs-lookup"><span data-stu-id="8aac3-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="8aac3-105">La présence d’un code inutile indique l’un des problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="8aac3-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="8aac3-106">Lisibilité : code qui dégrade inutilement la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="8aac3-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="8aac3-107">Par exemple, [IDE0001](ide0001.md) signale les qualifications de nom de type inutiles.</span><span class="sxs-lookup"><span data-stu-id="8aac3-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="8aac3-108">Maintenabilité : le code qui n’est plus utilisé après la refactorisation et est inutilement géré.</span><span class="sxs-lookup"><span data-stu-id="8aac3-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="8aac3-109">Par exemple, [IDE0051](ide0051.md) signale les champs, les propriétés, les événements et les méthodes privés inutilisés.</span><span class="sxs-lookup"><span data-stu-id="8aac3-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="8aac3-110">Performances : calcul inutile qui n’a pas d’effets secondaires et entraîne une surcharge de performance inutile.</span><span class="sxs-lookup"><span data-stu-id="8aac3-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="8aac3-111">Par exemple, [IDE0059](ide0059.md) signale les assignations de valeurs inutilisées où l’expression pour calculer une valeur n’a aucun effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="8aac3-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="8aac3-112">Fonctionnalité : problème fonctionnel dans le code conduisant à un rendu redondant du code requis.</span><span class="sxs-lookup"><span data-stu-id="8aac3-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="8aac3-113">Par exemple, [IDE0060](ide0060.md) signale les paramètres inutilisés où la méthode ignore accidentellement un paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8aac3-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="8aac3-114">Les règles de cette section concernent les règles de code inutiles suivantes :</span><span class="sxs-lookup"><span data-stu-id="8aac3-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="8aac3-115">Simplifier le nom (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="8aac3-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="8aac3-116">Simplifier l’accès aux membres (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="8aac3-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="8aac3-117">Supprimer le cast inutile (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="8aac3-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="8aac3-118">Supprimer l’importation inutile (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="8aac3-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="8aac3-119">Supprimer le code inaccessible (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="8aac3-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="8aac3-120">Supprimer un membre privé inutilisé (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="8aac3-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="8aac3-121">Supprimer un membre privé non lu (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="8aac3-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="8aac3-122">Supprimer la valeur de l’expression inutilisée (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="8aac3-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="8aac3-123">Supprimer l’assignation de valeur inutile (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="8aac3-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="8aac3-124">Supprimer le paramètre inutilisé (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="8aac3-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="8aac3-125">Supprimer la suppression inutile (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="8aac3-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="8aac3-126">[Supprimez l’opérateur de suppression inutile (IDE0080)](ide0080.md) -C# uniquement.</span><span class="sxs-lookup"><span data-stu-id="8aac3-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="8aac3-127">[Supprimer « ByVal » (IDE0081)](ide0081.md) -Visual Basic uniquement.</span><span class="sxs-lookup"><span data-stu-id="8aac3-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="8aac3-128">Supprimer l’opérateur d’égalité inutile (IDE0100)</span><span class="sxs-lookup"><span data-stu-id="8aac3-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="8aac3-129">[Supprimer les suppressions inutiles (IDE0110)](ide0110.md) -C# uniquement.</span><span class="sxs-lookup"><span data-stu-id="8aac3-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="8aac3-130">Certaines de ces règles comportent des options pour configurer le comportement de la règle :</span><span class="sxs-lookup"><span data-stu-id="8aac3-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="8aac3-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="8aac3-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="8aac3-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="8aac3-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="8aac3-133">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="8aac3-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="8aac3-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="8aac3-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="8aac3-135">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="8aac3-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="8aac3-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="8aac3-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="8aac3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aac3-137">See also</span></span>

- [<span data-ttu-id="8aac3-138">Règles du langage de style de code</span><span class="sxs-lookup"><span data-stu-id="8aac3-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="8aac3-139">Référence des règles de style de code</span><span class="sxs-lookup"><span data-stu-id="8aac3-139">Code style rules reference</span></span>](index.md)
