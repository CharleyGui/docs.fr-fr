---
title: '#warning - Référence C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608527"
---
# <a name="warning-c-reference"></a><span data-ttu-id="d3ff7-102">#warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d3ff7-102">#warning (C# Reference)</span></span>
<span data-ttu-id="d3ff7-103">`#warning` vous permet de générer un avertissement du compilateur de premier niveau [CS1030](../../misc/cs1030.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="d3ff7-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="d3ff7-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d3ff7-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="d3ff7-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="d3ff7-105">Remarks</span></span>
 <span data-ttu-id="d3ff7-106">`#warning` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="d3ff7-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="d3ff7-107">Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="d3ff7-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ff7-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="d3ff7-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="d3ff7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ff7-109">See also</span></span>

- [<span data-ttu-id="d3ff7-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d3ff7-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d3ff7-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d3ff7-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d3ff7-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="d3ff7-112">C# Preprocessor Directives</span></span>](./index.md)
