---
title: '#elif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712570"
---
# <a name="elif-c-reference"></a>#elif (référence C#)
`#elif` vous permet de créer une directive conditionnelle composée. L’expression `#elif` est évaluée si ni l’expression [#if](./preprocessor-if.md) précédente ni une expression de directive `#elif` facultative précédente n’est évaluée à `true`. Si une expression `#elif` est évaluée à `true`, le compilateur évalue l’ensemble du code situé entre `#elif` et la directive conditionnelle suivante. Par exemple :  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Vous pouvez utiliser les opérateurs `==` (égalité), `!=` (inégalité) `&&` (et) et `||` (ou) pour évaluer plusieurs symboles. Vous pouvez également regrouper des symboles et des opérateurs à l’aide de parenthèses.  
  
## <a name="remarks"></a>Notes   
 `#elif` revient à utiliser :  
  
```csharp
#else  
#if  
```  
  
 `#elif` est plus simple à utiliser, car chaque expression `#if` a besoin d’une expression [#endif](./preprocessor-endif.md), alors qu’une expression `#elif` peut être utilisée sans expression `#endif` correspondante.  
  
 Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#elif`.  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur de CMD](./index.md)
