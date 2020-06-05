---
title: Le type de '<variablename>' ne peut pas être déduit, car les limites de la boucle et la clause d'incrémentation ne sont pas converties en un même type
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 74b690ce3dee87e481c629a254e629be4b40f8cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387008"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Le type de '\<variablename>' ne peut pas être déduit, car les limites de la boucle et la clause d'incrémentation ne sont pas converties en un même type

Vous avez écrit une `For...Next` boucle dans laquelle le compilateur ne peut pas déduire un type de données pour la variable de contrôle de boucle, car les conditions suivantes sont vraies :

- Le type de données de la variable de contrôle de boucle n’est pas spécifié avec une clause `As` .

- Les limites de la boucle et l’incrémentation contiennent au moins deux types de données.

- Il n’existe aucune conversion standard entre les types de données.

 Par conséquent, le compilateur ne peut pas déduire le type de données d’une variable de contrôle de boucle.

 Dans l’exemple suivant, la variable Step est un caractère et les limites de la boucle sont à la fois des entiers. Étant donné qu’il n’existe pas de conversion standard entre les caractères et les entiers, cette erreur est signalée.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**ID d’erreur :** BC30982

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Modifiez les types des limites de la boucle et de la variable d’étape si nécessaire afin qu’au moins l’un d’eux soit un type auquel les autres s’étendent. Dans l’exemple précédent, remplacez le type de `stepVar` par `Integer` .

  ```vb
  Dim stepVar = 1
  ```

  -ou-

  ```vb
  Dim stepVar As Integer = 1
  ```

- Utilisez des fonctions de conversion explicites pour convertir les limites de la boucle et la variable d’étape en types appropriés. Dans l’exemple précédent, appliquez la `Val` fonction à `stepVar` .

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next (instruction)](../statements/for-next-statement.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
- [Instruction Option Infer](../statements/option-infer-statement.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
