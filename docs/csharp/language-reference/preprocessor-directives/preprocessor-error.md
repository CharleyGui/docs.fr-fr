---
title: '#error - Référence C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812365"
---
# <a name="error-c-reference"></a>#error (référence C#)

`#error` vous permet de générer une erreur définie par l’utilisateur [CS1029](../compiler-messages/cs1029.md) à partir d’un emplacement spécifique dans votre code. Par exemple :

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> Le compilateur traite `#error version` de façon spéciale et signale une erreur du compilateur, CS8304, avec un message contenant le compilateur utilisé et les versions de langage.

## <a name="remarks"></a>Notes

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
