---
description: Checked et Unchecked - Référence C#
title: Checked et Unchecked - Référence C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138265"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="c130f-103">Checked et Unchecked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c130f-103">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="c130f-104">Les instructions C# peuvent s'exécuter dans un contexte vérifié (checked) ou non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="c130f-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="c130f-105">Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception.</span><span class="sxs-lookup"><span data-stu-id="c130f-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="c130f-106">Dans un contexte non vérifié (unchecked), ce dépassement de capacité arithmétique est ignoré et le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.</span><span class="sxs-lookup"><span data-stu-id="c130f-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="c130f-107">[checked](checked.md) Indique un contexte vérifié.</span><span class="sxs-lookup"><span data-stu-id="c130f-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="c130f-108">[unchecked](unchecked.md) Indique un contexte non vérifié.</span><span class="sxs-lookup"><span data-stu-id="c130f-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="c130f-109">Les opérations suivantes sont concernées par la vérification du dépassement de capacité :</span><span class="sxs-lookup"><span data-stu-id="c130f-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="c130f-110">Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :</span><span class="sxs-lookup"><span data-stu-id="c130f-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="c130f-111">`++`, `--`, unaire `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="c130f-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="c130f-112">Conversions numériques explicites entre types intégraux, ou de `float` ou `double` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="c130f-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="c130f-113">Si ni `checked` ni `unchecked` ne sont spécifiés, le contexte par défaut pour les expressions non constantes (expressions évaluées au moment de l’exécution) est défini par la valeur de l’option [-checked](../compiler-options/checked-compiler-option.md) compilateur.</span><span class="sxs-lookup"><span data-stu-id="c130f-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c130f-114">Par défaut, la valeur de cette option n’est pas définie et les opérations arithmétiques sont exécutées dans un contexte non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="c130f-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="c130f-115">Pour les expressions constantes (expressions pouvant être complètement évaluées au moment de la compilation), le contexte par défaut est toujours vérifié (checked).</span><span class="sxs-lookup"><span data-stu-id="c130f-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="c130f-116">Sauf si une expression constante est placée explicitement dans un contexte non vérifié (unchecked), les dépassements de capacité qui se produisent pendant l’évaluation lors de la compilation de l’expression entraînent des erreurs au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c130f-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c130f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c130f-117">See also</span></span>

- [<span data-ttu-id="c130f-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c130f-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c130f-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c130f-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c130f-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="c130f-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c130f-121">Mots clés d'instructions</span><span class="sxs-lookup"><span data-stu-id="c130f-121">Statement Keywords</span></span>](statement-keywords.md)
