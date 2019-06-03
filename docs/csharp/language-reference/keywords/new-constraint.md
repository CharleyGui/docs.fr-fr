---
title: new, contrainte - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 2aa68bec13322e332bfe3841bc99403f72301183
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421799"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="1f1cb-102">new, contrainte (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1f1cb-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="1f1cb-103">La contrainte `new` spécifie que tout argument de type dans une déclaration de classe générique doit avoir un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="1f1cb-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="1f1cb-104">Pour utiliser la contrainte new, le type ne doit pas être abstract.</span><span class="sxs-lookup"><span data-stu-id="1f1cb-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="1f1cb-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f1cb-105">Example</span></span>

<span data-ttu-id="1f1cb-106">Appliquez la contrainte `new` à un paramètre de type quand votre classe générique crée des instances du type, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1f1cb-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="1f1cb-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f1cb-107">Example</span></span>

<span data-ttu-id="1f1cb-108">Si vous utilisez la contrainte `new()` avec d’autres contraintes, spécifiez-la en dernier :</span><span class="sxs-lookup"><span data-stu-id="1f1cb-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="1f1cb-109">Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1f1cb-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1f1cb-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1f1cb-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1f1cb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f1cb-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="1f1cb-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1f1cb-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="1f1cb-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1f1cb-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f1cb-114">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1f1cb-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1f1cb-115">Génériques</span><span class="sxs-lookup"><span data-stu-id="1f1cb-115">Generics</span></span>](../../programming-guide/generics/index.md)
