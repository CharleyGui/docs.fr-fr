---
title: '#define - Référence C#'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173430"
---
# <a name="define-c-reference"></a>#define (référence C#)
Vous utilisez `#define` pour définir un symbole. Quand vous utilisez le symbole sous forme d’expression passée à la directive [#if](./preprocessor-if.md), l’expression donne la valeur `true`, comme illustré dans l’exemple suivant :  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> La directive `#define` ne peut pas être utilisée pour déclarer des valeurs constantes comme c’est le cas en général en C et C++. Les constantes en C# sont définies plutôt comme des membres statiques d’une classe ou d’un struct. Si vous avez plusieurs constantes de ce type, créez une classe « Constantes » distincte pour les stocker.  
  
 Les symboles peuvent être utilisés pour spécifier des conditions de compilation. Vous pouvez tester le symbole avec [#if](./preprocessor-if.md) ou [#elif](./preprocessor-elif.md). Vous pouvez également utiliser <xref:System.Diagnostics.ConditionalAttribute> pour effectuer une compilation conditionnelle.  
  
 Vous pouvez définir un symbole, mais vous ne pouvez pas attribuer de valeur à un symbole. La directive `#define` doit apparaître dans le fichier avant l’utilisation d’instructions qui ne sont pas également des directives de préprocesseur.  
  
 Vous pouvez également définir un symbole avec l’option [compilateur-définir.](../compiler-options/define-compiler-option.md) Vous pouvez annuler la définition d’un symbole avec [#undef](./preprocessor-undef.md).  
  
 Un symbole que vous définissez avec `-define` ou `#define` n’est pas en conflit avec une variable du même nom. Autrement dit, un nom de variable ne doit pas être passé à une directive de préprocesseur et un symbole ne peut être évalué que par une directive de préprocesseur.  
  
 La portée d’un symbole qui a été créé à l’aide de `#define` est le fichier dans lequel le symbole a été défini.  
  
 Comme le montre l’exemple suivant, vous devez placer les directives `#define` en haut du fichier.  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Pour obtenir un exemple montrant comment annuler la définition d’un symbole, consultez [#undef](./preprocessor-undef.md).  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur de CMD](./index.md)
- [const](../keywords/const.md)
- [Comment : effectuer une compilation conditionnelle avec Trace et Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
