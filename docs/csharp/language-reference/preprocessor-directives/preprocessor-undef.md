---
description: '#undef - Référence sur C#'
title: '#undef - Référence sur C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150555"
---
# <a name="undef-c-reference"></a><span data-ttu-id="b6d78-103">#undef (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b6d78-103">#undef (C# Reference)</span></span>

<span data-ttu-id="b6d78-104">`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](./preprocessor-if.md), l’expression correspond à `false`.</span><span class="sxs-lookup"><span data-stu-id="b6d78-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="b6d78-105">Un symbole peut être défini à l’aide de la directive [#define](./preprocessor-define.md) ou de l’option [de compilateur-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="b6d78-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b6d78-106">La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.</span><span class="sxs-lookup"><span data-stu-id="b6d78-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6d78-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6d78-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="b6d78-108">**DEBUG n’est pas défini**</span><span class="sxs-lookup"><span data-stu-id="b6d78-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="b6d78-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6d78-109">See also</span></span>

- [<span data-ttu-id="b6d78-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b6d78-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b6d78-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b6d78-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b6d78-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="b6d78-112">C# Preprocessor Directives</span></span>](./index.md)
