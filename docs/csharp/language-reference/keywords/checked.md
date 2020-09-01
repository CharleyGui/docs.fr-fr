---
description: checked, mot clé - Référence C#
title: checked, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 4dd8bc02d3af89d6bab3aef55a88cb8b40704da6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138278"
---
# <a name="checked-c-reference"></a><span data-ttu-id="c7ecb-103">checked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c7ecb-103">checked (C# Reference)</span></span>

<span data-ttu-id="c7ecb-104">Le mot clé `checked` permet d’activer explicitement le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-104">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="c7ecb-105">Par défaut, une expression qui contient uniquement des valeurs constantes provoque une erreur du compilateur si l’expression produit une valeur située en dehors de la plage du type de destination.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-105">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="c7ecb-106">Si l’expression contient une ou plusieurs valeurs non constantes, le compilateur ne détecte pas le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-106">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="c7ecb-107">L’évaluation de l’expression assignée à `i2` dans l’exemple suivant ne provoque pas d’erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-107">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

<span data-ttu-id="c7ecb-108">Par défaut, ces expressions non constantes ne font pas l’objet d’une vérification d’un dépassement de capacité au moment de l’exécution et ne lèvent aucune exception de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-108">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="c7ecb-109">L’exemple précédent affiche -2 147 483 639 comme somme de deux entiers positifs.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-109">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>

<span data-ttu-id="c7ecb-110">Le contrôle de dépassement de capacité peut être activé par les options du compilateur, la configuration de l’environnement ou l’utilisation du mot clé `checked`.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-110">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="c7ecb-111">Les exemples suivants montrent comment utiliser une expression `checked` ou un bloc `checked` pour détecter le dépassement de capacité produit par la somme précédente au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-111">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="c7ecb-112">Les deux exemples lèvent une exception de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-112">Both examples raise an overflow exception.</span></span>

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

<span data-ttu-id="c7ecb-113">Vous pouvez utiliser le mot clé [unchecked](./unchecked.md) pour empêcher la vérification du dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-113">The [unchecked](./unchecked.md) keyword can be used to prevent overflow checking.</span></span>

## <a name="example"></a><span data-ttu-id="c7ecb-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7ecb-114">Example</span></span>

<span data-ttu-id="c7ecb-115">Cet exemple montre comment utiliser `checked` pour activer la vérification du dépassement de capacité au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-115">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="c7ecb-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c7ecb-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c7ecb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7ecb-117">See also</span></span>

- [<span data-ttu-id="c7ecb-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c7ecb-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7ecb-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c7ecb-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7ecb-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="c7ecb-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c7ecb-121">Checked et unchecked</span><span class="sxs-lookup"><span data-stu-id="c7ecb-121">Checked and Unchecked</span></span>](./checked-and-unchecked.md)
- [<span data-ttu-id="c7ecb-122">unchecked</span><span class="sxs-lookup"><span data-stu-id="c7ecb-122">unchecked</span></span>](./unchecked.md)
