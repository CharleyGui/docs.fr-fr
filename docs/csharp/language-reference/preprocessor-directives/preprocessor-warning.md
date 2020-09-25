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
# <a name="warning-c-reference"></a>#warning (référence C#)

`#warning` vous permet de générer un avertissement du compilateur de premier niveau [CS1030](../../misc/cs1030.md) à partir d’un emplacement spécifique dans votre code. Par exemple :  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Notes

 `#warning` est souvent utilisé dans une directive conditionnelle. Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](./preprocessor-error.md).  
  
## <a name="example"></a>Exemple  

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

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
