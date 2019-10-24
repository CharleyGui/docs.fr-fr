---
title: Checked et Unchecked - Référence C#
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771773"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="4a735-102">Checked et Unchecked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4a735-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="4a735-103">Les instructions C# peuvent s'exécuter dans un contexte vérifié (checked) ou non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="4a735-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="4a735-104">Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception.</span><span class="sxs-lookup"><span data-stu-id="4a735-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="4a735-105">Dans un contexte non vérifié (unchecked), ce dépassement de capacité arithmétique est ignoré et le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.</span><span class="sxs-lookup"><span data-stu-id="4a735-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="4a735-106">[checked](checked.md) Indique un contexte vérifié.</span><span class="sxs-lookup"><span data-stu-id="4a735-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="4a735-107">[unchecked](unchecked.md) Indique un contexte non vérifié.</span><span class="sxs-lookup"><span data-stu-id="4a735-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="4a735-108">Les opérations suivantes sont concernées par la vérification du dépassement de capacité :</span><span class="sxs-lookup"><span data-stu-id="4a735-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="4a735-109">Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :</span><span class="sxs-lookup"><span data-stu-id="4a735-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="4a735-110">`++`, `--`, unaire `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="4a735-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="4a735-111">Conversions numériques explicites entre types intégraux, ou de `float` ou `double` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="4a735-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="4a735-112">Si ni `checked` ni `unchecked` ne sont spécifiés, le contexte par défaut pour les expressions non constantes (expressions évaluées au moment de l’exécution) est défini par la valeur de l’option [-checked](../compiler-options/checked-compiler-option.md) compilateur.</span><span class="sxs-lookup"><span data-stu-id="4a735-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="4a735-113">Par défaut, la valeur de cette option n’est pas définie et les opérations arithmétiques sont exécutées dans un contexte non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="4a735-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="4a735-114">Pour les expressions constantes (expressions pouvant être complètement évaluées au moment de la compilation), le contexte par défaut est toujours vérifié (checked).</span><span class="sxs-lookup"><span data-stu-id="4a735-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="4a735-115">Sauf si une expression constante est placée explicitement dans un contexte non vérifié (unchecked), les dépassements de capacité qui se produisent pendant l’évaluation lors de la compilation de l’expression entraînent des erreurs au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="4a735-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4a735-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a735-116">See also</span></span>

- [<span data-ttu-id="4a735-117">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="4a735-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a735-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4a735-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a735-119">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4a735-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4a735-120">Mots clés d’instructions</span><span class="sxs-lookup"><span data-stu-id="4a735-120">Statement Keywords</span></span>](statement-keywords.md)
