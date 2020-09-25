---
description: '#warning - Référence C#'
title: '#warning - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 9ade723bdca17597dcd56240f506e60f2debf6be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186417"
---
# <a name="warning-c-reference"></a><span data-ttu-id="fa255-103">#warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="fa255-103">#warning (C# Reference)</span></span>

<span data-ttu-id="fa255-104">`#warning` vous permet de générer un avertissement du compilateur de premier niveau [CS1030](../../misc/cs1030.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="fa255-104">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="fa255-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="fa255-105">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="fa255-106">Notes</span><span class="sxs-lookup"><span data-stu-id="fa255-106">Remarks</span></span>

 <span data-ttu-id="fa255-107">`#warning` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="fa255-107">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="fa255-108">Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="fa255-108">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa255-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fa255-109">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="fa255-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa255-110">See also</span></span>

- [<span data-ttu-id="fa255-111">Référence C#</span><span class="sxs-lookup"><span data-stu-id="fa255-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fa255-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fa255-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fa255-113">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="fa255-113">C# Preprocessor Directives</span></span>](./index.md)
