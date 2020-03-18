---
title: '#warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715069"
---
# <a name="warning-c-reference"></a><span data-ttu-id="5e83c-102">#warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5e83c-102">#warning (C# Reference)</span></span>
<span data-ttu-id="5e83c-103">`#warning` vous permet de générer un avertissement du compilateur de premier niveau [CS1030](../../misc/cs1030.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5e83c-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="5e83c-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5e83c-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e83c-105">Notes </span><span class="sxs-lookup"><span data-stu-id="5e83c-105">Remarks</span></span>
 <span data-ttu-id="5e83c-106">`#warning` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="5e83c-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="5e83c-107">Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="5e83c-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e83c-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5e83c-108">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="5e83c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e83c-109">See also</span></span>

- [<span data-ttu-id="5e83c-110">Référence C</span><span class="sxs-lookup"><span data-stu-id="5e83c-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e83c-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5e83c-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e83c-112">Directives de préprocesseur de CMD</span><span class="sxs-lookup"><span data-stu-id="5e83c-112">C# Preprocessor Directives</span></span>](./index.md)
