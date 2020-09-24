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
# <a name="undef-c-reference"></a>#undef (référence C#)

`#undef` vous permet d’annuler la définition d’un symbole de telle sorte qu’en utilisant le symbole comme expression dans une directive [#if](./preprocessor-if.md), l’expression correspond à `false`.  
  
 Un symbole peut être défini à l’aide de la directive [#define](./preprocessor-define.md) ou de l’option [de compilateur-define](../compiler-options/define-compiler-option.md) . La directive `#undef` doit figurer dans le fichier préalablement à l’utilisation d’instructions qui ne sont pas aussi des directives.  
  
## <a name="example"></a>Exemple  

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

**DEBUG n’est pas défini**

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
