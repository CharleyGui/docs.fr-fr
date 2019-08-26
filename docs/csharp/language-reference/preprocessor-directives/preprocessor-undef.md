---
title: '#undef - Référence sur C#'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605587"
---
# <a name="undef-c-reference"></a><span data-ttu-id="25a81-102">#undef (référence C#)</span><span class="sxs-lookup"><span data-stu-id="25a81-102">#undef (C# Reference)</span></span>
<span data-ttu-id="25a81-103">`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](./preprocessor-if.md), l’expression correspond à `false`.</span><span class="sxs-lookup"><span data-stu-id="25a81-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="25a81-104">Un symbole peut être défini avec la directive [#define](./preprocessor-define.md) ou l’option du compilateur [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="25a81-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="25a81-105">La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.</span><span class="sxs-lookup"><span data-stu-id="25a81-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25a81-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="25a81-106">Example</span></span>  

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

<span data-ttu-id="25a81-107">**DEBUG n’est pas défini**</span><span class="sxs-lookup"><span data-stu-id="25a81-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="25a81-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25a81-108">See also</span></span>

- [<span data-ttu-id="25a81-109">Référence C#</span><span class="sxs-lookup"><span data-stu-id="25a81-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25a81-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="25a81-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="25a81-111">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="25a81-111">C# Preprocessor Directives</span></span>](./index.md)
