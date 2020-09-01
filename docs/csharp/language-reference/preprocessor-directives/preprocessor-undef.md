---
description: '#undef - Référence sur C#'
title: '#undef - Référence sur C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 97f99ab4230585e61fed0e057552b78c7a4c2bb5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137862"
---
# <a name="undef-c-reference"></a><span data-ttu-id="baa74-103">#undef (référence C#)</span><span class="sxs-lookup"><span data-stu-id="baa74-103">#undef (C# Reference)</span></span>
<span data-ttu-id="baa74-104">`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](./preprocessor-if.md), l’expression correspond à `false`.</span><span class="sxs-lookup"><span data-stu-id="baa74-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="baa74-105">Un symbole peut être défini à l’aide de la directive [#define](./preprocessor-define.md) ou de l’option [de compilateur-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="baa74-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="baa74-106">La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.</span><span class="sxs-lookup"><span data-stu-id="baa74-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa74-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="baa74-107">Example</span></span>  

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

<span data-ttu-id="baa74-108">**DEBUG n’est pas défini**</span><span class="sxs-lookup"><span data-stu-id="baa74-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="baa74-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baa74-109">See also</span></span>

- [<span data-ttu-id="baa74-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="baa74-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="baa74-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="baa74-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="baa74-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="baa74-112">C# Preprocessor Directives</span></span>](./index.md)
