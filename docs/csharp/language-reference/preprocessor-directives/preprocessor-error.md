---
title: '#error - Référence C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812365"
---
# <a name="error-c-reference"></a><span data-ttu-id="cdab3-102">#error (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cdab3-102">#error (C# Reference)</span></span>

<span data-ttu-id="cdab3-103">`#error` vous permet de générer une erreur définie par l’utilisateur [CS1029](../compiler-messages/cs1029.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="cdab3-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="cdab3-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cdab3-104">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="cdab3-105">Le compilateur traite `#error version` de façon spéciale et signale une erreur du compilateur, CS8304, avec un message contenant le compilateur utilisé et les versions de langage.</span><span class="sxs-lookup"><span data-stu-id="cdab3-105">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdab3-106">Notes</span><span class="sxs-lookup"><span data-stu-id="cdab3-106">Remarks</span></span>

<span data-ttu-id="cdab3-107">`#error` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="cdab3-107">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="cdab3-108">Il est possible aussi de générer un avertissement défini par l’utilisateur avec [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="cdab3-108">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="cdab3-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="cdab3-109">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cdab3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdab3-110">See also</span></span>

- [<span data-ttu-id="cdab3-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cdab3-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cdab3-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cdab3-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cdab3-113">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="cdab3-113">C# Preprocessor Directives</span></span>](./index.md)
