---
title: '#error - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712518"
---
# <a name="error-c-reference"></a><span data-ttu-id="cabf5-102">#error (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cabf5-102">#error (C# Reference)</span></span>
<span data-ttu-id="cabf5-103">`#error` vous permet de générer une erreur définie par l’utilisateur [CS1029](../compiler-messages/cs1029.md) à partir d’un emplacement spécifique dans votre code.</span><span class="sxs-lookup"><span data-stu-id="cabf5-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="cabf5-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cabf5-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="cabf5-105">Notes</span><span class="sxs-lookup"><span data-stu-id="cabf5-105">Remarks</span></span>  
 <span data-ttu-id="cabf5-106">`#error` est souvent utilisé dans une directive conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="cabf5-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="cabf5-107">Il est possible aussi de générer un avertissement défini par l’utilisateur avec [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="cabf5-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cabf5-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="cabf5-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cabf5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cabf5-109">See also</span></span>

- [<span data-ttu-id="cabf5-110">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cabf5-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cabf5-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cabf5-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cabf5-112">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="cabf5-112">C# Preprocessor Directives</span></span>](./index.md)
