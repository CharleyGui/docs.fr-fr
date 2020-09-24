---
description: '#endif - Référence C#'
title: '#endif - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 0ccc00ceab2aa67c77140e3ef09907ba260d7e9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168632"
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

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
