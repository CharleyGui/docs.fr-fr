---
title: Facultatif
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: c46d06dba61158d7362d736731161be306af3f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392143"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)

Spécifie qu’un argument de procédure peut être omis lorsque la procédure est appelée.

## <a name="remarks"></a>Notes

Pour chaque paramètre facultatif, vous devez spécifier une expression constante comme valeur par défaut de ce paramètre. Si l’expression prend la valeur [Nothing](../nothing.md), la valeur par défaut du type de données value est utilisée comme valeur par défaut du paramètre.

Si la liste de paramètres contient un paramètre facultatif, chaque paramètre qui le suit doit également être facultatif.

Le modificateur `Optional` peut être utilisé dans les contextes suivants :

- [Declare Statement](../statements/declare-statement.md)

- [Function (instruction)](../statements/function-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub (instruction)](../statements/sub-statement.md)

> [!NOTE]
> Lors de l’appel d’une procédure avec ou sans paramètres facultatifs, vous pouvez passer des arguments par position ou par nom. Pour plus d’informations, consultez [passage des arguments par position et par nom](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).

> [!NOTE]
> Vous pouvez également définir une procédure avec des paramètres facultatifs à l’aide de la surcharge. Si vous avez un paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, une qui accepte le paramètre et une autre qui ne l’est pas. Pour plus d'informations, consultez [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).

## <a name="example"></a>Exemple

L’exemple suivant définit une procédure qui a un paramètre facultatif.

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment appeler une procédure avec des arguments passés par position et avec des arguments passés par nom. La procédure a deux paramètres facultatifs.

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>Voir aussi

- [Liste de paramètres](../statements/parameter-list.md)
- [Paramètres facultatifs](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Mots clés](../keywords/index.md)
