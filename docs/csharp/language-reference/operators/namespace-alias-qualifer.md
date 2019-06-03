---
title: ::, opérateur - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422524"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d32cd-102">::, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d32cd-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="d32cd-103">Le qualificateur d’alias d’espace de noms (`::`) s’utilise pour rechercher les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="d32cd-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="d32cd-104">Il se place toujours entre deux identificateurs, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="d32cd-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="d32cd-105">L’opérateur `::` peut également être utilisé avec une *directive d’alias using* :</span><span class="sxs-lookup"><span data-stu-id="d32cd-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="d32cd-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="d32cd-106">Remarks</span></span>

<span data-ttu-id="d32cd-107">Le qualificateur d’alias d’espace de noms peut être `global`.</span><span class="sxs-lookup"><span data-stu-id="d32cd-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="d32cd-108">Il appelle alors une recherche dans l’espace de noms global, plutôt que dans un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="d32cd-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="d32cd-109">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="d32cd-109">For more information</span></span>

<span data-ttu-id="d32cd-110">Pour obtenir un exemple d’utilisation de l’opérateur `::`, consultez la section suivante :</span><span class="sxs-lookup"><span data-stu-id="d32cd-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="d32cd-111">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="d32cd-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="d32cd-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d32cd-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d32cd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d32cd-113">See also</span></span>

- [<span data-ttu-id="d32cd-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d32cd-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d32cd-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d32cd-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d32cd-116">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d32cd-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="d32cd-117">., opérateur</span><span class="sxs-lookup"><span data-stu-id="d32cd-117">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="d32cd-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="d32cd-118">extern alias</span></span>](../keywords/extern-alias.md)
