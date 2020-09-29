---
description: partial, type - Référence C#
title: partial, type - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4e73b34390143a2ac9b839e1da79b7894232c4b4
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437880"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="9944a-103">partial, type (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9944a-103">partial type (C# Reference)</span></span>

<span data-ttu-id="9944a-104">Les définitions de type partiel permettent de fractionner en plusieurs fichiers la définition d’une classe, d’une structure, d’une interface ou d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="9944a-104">Partial type definitions allow for the definition of a class, struct, interface, or record to be split into multiple files.</span></span>

<span data-ttu-id="9944a-105">Dans *file1.cs*:</span><span class="sxs-lookup"><span data-stu-id="9944a-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="9944a-106">Dans *file2.cs* , la déclaration :</span><span class="sxs-lookup"><span data-stu-id="9944a-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="9944a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9944a-107">Remarks</span></span>

<span data-ttu-id="9944a-108">Fractionner un type de classe, de struct ou d’interface entre plusieurs fichiers peut être utile si vous travaillez sur des projets volumineux ou des projets contenant du code généré automatiquement, comme celui fourni par le [Concepteur Windows Forms](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span><span class="sxs-lookup"><span data-stu-id="9944a-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span></span> <span data-ttu-id="9944a-109">Un type partiel peut contenir une [méthode partielle](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="9944a-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="9944a-110">Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9944a-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9944a-111">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9944a-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9944a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9944a-112">See also</span></span>

- [<span data-ttu-id="9944a-113">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9944a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9944a-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9944a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9944a-115">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="9944a-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9944a-116">Introduction aux génériques</span><span class="sxs-lookup"><span data-stu-id="9944a-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
