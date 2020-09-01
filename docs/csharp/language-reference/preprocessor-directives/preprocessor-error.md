---
description: '#error - Référence C#'
title: '#error - Référence C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138096"
---
# <a name="error-c-reference"></a>#error (référence C#)

`#error` vous permet de générer une erreur définie par l’utilisateur [CS1029](../compiler-messages/cs1029.md) à partir d’un emplacement spécifique dans votre code. Par exemple :

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> Le compilateur traite `#error version` de façon spéciale et signale une erreur du compilateur, CS8304, avec un message contenant le compilateur utilisé et les versions de langage.

## <a name="remarks"></a>Remarques

`#error` est souvent utilisé dans une directive conditionnelle.

Il est possible aussi de générer un avertissement défini par l’utilisateur avec [#warning](./preprocessor-warning.md).

## <a name="example"></a>Exemple

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

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
