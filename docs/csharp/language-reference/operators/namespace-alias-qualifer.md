---
title: 'Opérateur :: - Référence C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025072"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="db8e4-102">Opérateur :: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="db8e4-102">:: operator (C# reference)</span></span>

<span data-ttu-id="db8e4-103">Le qualificateur d’alias d’espace de noms (`::`) s’utilise pour rechercher les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="db8e4-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="db8e4-104">Il se place toujours entre deux identificateurs, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="db8e4-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="db8e4-105">L’opérateur `::` peut également être utilisé avec une *directive d’alias using* :</span><span class="sxs-lookup"><span data-stu-id="db8e4-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="db8e4-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="db8e4-106">Remarks</span></span>

<span data-ttu-id="db8e4-107">Le qualificateur d’alias d’espace de noms peut être `global`.</span><span class="sxs-lookup"><span data-stu-id="db8e4-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="db8e4-108">Il appelle alors une recherche dans l’espace de noms global, plutôt que dans un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="db8e4-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="db8e4-109">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="db8e4-109">For more information</span></span>

<span data-ttu-id="db8e4-110">Pour obtenir un exemple d’utilisation de l’opérateur `::`, consultez la section suivante :</span><span class="sxs-lookup"><span data-stu-id="db8e4-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="db8e4-111">Guide pratique pour utiliser l’alias d’espace de noms global</span><span class="sxs-lookup"><span data-stu-id="db8e4-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="db8e4-112">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="db8e4-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="db8e4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db8e4-113">See also</span></span>

- [<span data-ttu-id="db8e4-114">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="db8e4-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db8e4-115">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="db8e4-115">C# operators</span></span>](index.md)
- [<span data-ttu-id="db8e4-116">., opérateur</span><span class="sxs-lookup"><span data-stu-id="db8e4-116">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="db8e4-117">extern alias</span><span class="sxs-lookup"><span data-stu-id="db8e4-117">extern alias</span></span>](../keywords/extern-alias.md)
