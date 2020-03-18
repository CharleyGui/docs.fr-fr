---
title: partial, type - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715206"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="7feb1-102">partial, type (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7feb1-102">partial type (C# Reference)</span></span>

<span data-ttu-id="7feb1-103">Les définitions de type partiel permettent le fractionnement de la définition d’une classe, d’un struct ou d’une interface entre plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="7feb1-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="7feb1-104">En *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="7feb1-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="7feb1-105">Dans *File2.cs* la déclaration :</span><span class="sxs-lookup"><span data-stu-id="7feb1-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="7feb1-106">Notes </span><span class="sxs-lookup"><span data-stu-id="7feb1-106">Remarks</span></span>

<span data-ttu-id="7feb1-107">Fractionner un type de classe, de struct ou d’interface entre plusieurs fichiers peut être utile si vous travaillez sur des projets volumineux ou des projets contenant du code généré automatiquement, comme celui fourni par le [Concepteur Windows Forms](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7feb1-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="7feb1-108">Un type partiel peut contenir une [méthode partielle](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="7feb1-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="7feb1-109">Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7feb1-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7feb1-110">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7feb1-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7feb1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7feb1-111">See also</span></span>

- [<span data-ttu-id="7feb1-112">Référence C</span><span class="sxs-lookup"><span data-stu-id="7feb1-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7feb1-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7feb1-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7feb1-114">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="7feb1-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7feb1-115">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="7feb1-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
