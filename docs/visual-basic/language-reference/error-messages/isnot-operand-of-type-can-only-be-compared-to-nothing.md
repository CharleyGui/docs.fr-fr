---
title: L’opérande 'IsNot' du type 'NomType' ne peut être comparé qu’à 'Nothing', car 'NomType' est un type nullable
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524373"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>L’opérande 'IsNot' du type 'NomType' ne peut être comparé qu’à 'Nothing', car 'NomType' est un type nullable

Une variable déclarée comme Nullable a été comparée à une expression autre que `Nothing` à l’aide de l’opérateur `IsNot`.

**ID d’erreur :** BC32128

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Pour comparer un type nullable à une expression autre que `Nothing` à l’aide de l’opérateur `IsNot` , appelez la méthode `GetType` sur le type nullable et comparez le résultat à l’expression, comme illustré dans l’exemple suivant.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
