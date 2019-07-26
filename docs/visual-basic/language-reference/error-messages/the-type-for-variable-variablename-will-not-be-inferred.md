---
title: Le type pour la variable '<variablename>' ne sera pas déduit, car il est lié à un champ d'une portée englobante
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512723"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Le type de la variable\<'VariableName > 'ne sera pas déduit, car il est lié à un champ dans une portée englobante

Le type de la variable\<'VariableName > 'ne sera pas déduit, car il est lié à un champ dans une portée englobante. Modifiez le nom de'\<VariableName > 'ou utilisez le nom complet (par exemple, 'me. NomVariable’ou’MyBase. NomVariable').

Une variable de contrôle de boucle dans votre code porte le même nom qu’un champ de la classe ou d’une autre portée englobante. Étant donné que la variable de contrôle est `As` utilisée sans clause, elle est liée au champ dans la portée englobante, et le compilateur ne crée pas de variable pour celle-ci ou ne déduit pas son type.

Dans l’exemple suivant, `Index`la variable de contrôle de l' `For` instruction est liée au `Index` champ de la `Customer` classe. Le compilateur ne crée pas de variable pour la variable `Index` de contrôle ou ne déduit pas son type.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID d’erreur:** BC42110

### <a name="to-address-this-warning"></a>Pour traiter cet avertissement

- Rendez la variable de contrôle de boucle locale en remplaçant son nom par un identificateur qui n’est pas également le nom d’un champ de la classe.

  ```vb
  For I = 1 To 10
  ```

- Précisez que la variable de contrôle de boucle est liée au champ de classe `Me.` en préfixant le nom de la variable.

  ```vb
  For Me.Index = 1 To 10
  ```

- Au lieu de vous appuyer sur l’inférence de type local `As` , utilisez une clause pour spécifier un type pour la variable de contrôle de boucle.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>Exemple
 Le code suivant montre l’exemple précédent avec la première correction sur place.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>Voir aussi

- [Option Infer (instruction)](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Guide pratique pour Faire référence à l’instance actuelle d’un objet](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
