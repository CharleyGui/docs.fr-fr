---
description: '#error - Référence C#'
title: '#error - Référence C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138096"
---
# <a name="error-c-reference"></a><span data-ttu-id="76d6f-103">#error (référence C#)</span><span class="sxs-lookup"><span data-stu-id="76d6f-103">#error (C# Reference)</span></span>

<span data-ttu-id="76d6f-104">`#error` vous permet de générer une erreur définie par l’utilisateur [CS1029](../compiler-messages/cs1029.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="76d6f-104">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="76d6f-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="76d6f-105">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="76d6f-106">Le compilateur traite `#error version` de façon spéciale et signale une erreur du compilateur, CS8304, avec un message contenant le compilateur utilisé et les versions de langage.</span><span class="sxs-lookup"><span data-stu-id="76d6f-106">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="76d6f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="76d6f-107">Remarks</span></span>

<span data-ttu-id="76d6f-108">`#error` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="76d6f-108">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="76d6f-109">Il est possible aussi de générer un avertissement défini par l’utilisateur avec [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="76d6f-109">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="76d6f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="76d6f-110">Example</span></span>

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a><span data-ttu-id="76d6f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76d6f-111">See also</span></span>

- [<span data-ttu-id="76d6f-112">Référence C#</span><span class="sxs-lookup"><span data-stu-id="76d6f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="76d6f-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="76d6f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="76d6f-114">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="76d6f-114">C# Preprocessor Directives</span></span>](./index.md)
