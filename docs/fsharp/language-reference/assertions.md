---
title: Assertions
description: Découvrez comment utiliser l’expression’Assert’en tant que fonctionnalité de débogage pour tester des expressions F# dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630028"
---
# <a name="assertions"></a><span data-ttu-id="89229-103">Assertions</span><span class="sxs-lookup"><span data-stu-id="89229-103">Assertions</span></span>

<span data-ttu-id="89229-104">L' `assert` expression est une fonctionnalité de débogage que vous pouvez utiliser pour tester une expression.</span><span class="sxs-lookup"><span data-stu-id="89229-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="89229-105">En cas d’échec en mode débogage, une assertion génère une boîte de dialogue d’erreur système.</span><span class="sxs-lookup"><span data-stu-id="89229-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="89229-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89229-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="89229-107">Notes</span><span class="sxs-lookup"><span data-stu-id="89229-107">Remarks</span></span>

<span data-ttu-id="89229-108">L' `assert` expression a le `bool -> unit`type.</span><span class="sxs-lookup"><span data-stu-id="89229-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="89229-109">Dans la syntaxe précédente, *condition* représente une expression booléenne qui doit être testée.</span><span class="sxs-lookup"><span data-stu-id="89229-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="89229-110">Si l’expression prend la valeur `true`, l’exécution ne se poursuit pas.</span><span class="sxs-lookup"><span data-stu-id="89229-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="89229-111">Si la valeur `false`est, une boîte de dialogue d’erreur système est générée.</span><span class="sxs-lookup"><span data-stu-id="89229-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="89229-112">La boîte de dialogue d’erreur contient une légende qui indique que l’assertion de chaîne **a échoué**.</span><span class="sxs-lookup"><span data-stu-id="89229-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="89229-113">La boîte de dialogue contient une trace de la pile qui indique où l’échec de l’assertion s’est produit.</span><span class="sxs-lookup"><span data-stu-id="89229-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="89229-114">La vérification des assertions n’est activée que lorsque vous compilez en mode débogage; autrement dit, si la constante `DEBUG` est définie.</span><span class="sxs-lookup"><span data-stu-id="89229-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="89229-115">Dans le système de projet, par défaut, `DEBUG` la constante est définie dans la configuration Debug, mais pas dans la configuration Release.</span><span class="sxs-lookup"><span data-stu-id="89229-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="89229-116">L’erreur d’échec d’assertion ne peut pas F# être interceptée à l’aide de la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="89229-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="89229-117">La `assert` fonction est résolue en <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89229-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="89229-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="89229-118">Example</span></span>

<span data-ttu-id="89229-119">L’exemple de code suivant illustre l’utilisation de l' `assert` expression.</span><span class="sxs-lookup"><span data-stu-id="89229-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="89229-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89229-120">See also</span></span>

- [<span data-ttu-id="89229-121">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="89229-121">F# Language Reference</span></span>](index.md)
