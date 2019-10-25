---
title: Assertions
description: Découvrez comment utiliser l’expression’Assert’en tant que fonctionnalité de débogage pour tester des expressions F# dans le langage de programmation.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799064"
---
# <a name="assertions"></a><span data-ttu-id="0f441-103">Assertions</span><span class="sxs-lookup"><span data-stu-id="0f441-103">Assertions</span></span>

<span data-ttu-id="0f441-104">L’expression `assert` est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression.</span><span class="sxs-lookup"><span data-stu-id="0f441-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="0f441-105">En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.</span><span class="sxs-lookup"><span data-stu-id="0f441-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f441-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f441-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="0f441-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0f441-107">Remarks</span></span>

<span data-ttu-id="0f441-108">L’expression `assert` a le type `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="0f441-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="0f441-109">La fonction `assert` se résout en <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f441-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f441-110">Cela signifie que son comportement est identique à l’appel de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directement.</span><span class="sxs-lookup"><span data-stu-id="0f441-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="0f441-111">La vérification des assertions n’est activée que lorsque vous compilez en mode débogage ; autrement dit, si la constante `DEBUG` est définie.</span><span class="sxs-lookup"><span data-stu-id="0f441-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="0f441-112">Dans le système de projet, par défaut, la constante `DEBUG` est définie dans la configuration Debug, mais pas dans la configuration Release.</span><span class="sxs-lookup"><span data-stu-id="0f441-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="0f441-113">L’erreur d’échec d’assertion ne peut pas F# être interceptée à l’aide de la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="0f441-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="0f441-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f441-114">Example</span></span>

<span data-ttu-id="0f441-115">L’exemple de code suivant illustre l’utilisation de l’expression `assert`.</span><span class="sxs-lookup"><span data-stu-id="0f441-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="0f441-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f441-116">See also</span></span>

- [<span data-ttu-id="0f441-117">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="0f441-117">F# Language Reference</span></span>](index.md)
