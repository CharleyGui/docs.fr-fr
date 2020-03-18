---
title: '#endif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712544"
---
# <a name="endif-c-reference"></a>#endif (référence C#)
`#endif` spécifie la fin d’une directive conditionnelle, qui a commencé avec la directive [#if](./preprocessor-if.md). Par exemple,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Notes   
 Une directive conditionnelle commençant par une directive `#if` doit se terminer explicitement par une directive `#endif`. Consultez [#if](./preprocessor-if.md) pour obtenir un exemple d’utilisation de `#endif`.  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur de CMD](./index.md)
