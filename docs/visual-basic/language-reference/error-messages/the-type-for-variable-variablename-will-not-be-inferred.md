---
title: Le type pour la variable '<variablename>' ne sera pas déduit, car il est lié à un champ d'une portée englobante
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 3e76ffea283de2843fc5586179074c01a053ece8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161281"
---
# <a name="bc42110-the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>BC42110 : le type de la variable' \<variablename> 'ne sera pas déduit, car il est lié à un champ dans une portée englobante

Le type de la variable' \<variablename> 'ne sera pas déduit, car il est lié à un champ dans une portée englobante. Modifiez le nom de « \<variablename> » ou utilisez le nom complet (par exemple, « me. NomVariable » ou « MyBase. NomVariable »).

Une variable de contrôle de boucle dans votre code porte le même nom qu’un champ de la classe ou d’une autre portée englobante. Étant donné que la variable de contrôle est utilisée sans `As` clause, elle est liée au champ dans la portée englobante, et le compilateur ne crée pas de variable pour celle-ci ou ne déduit pas son type.

Dans l’exemple suivant, `Index` la variable de contrôle de l' `For` instruction est liée au `Index` champ de la `Customer` classe. Le compilateur ne crée pas de variable pour la variable de contrôle `Index` ou ne déduit pas son type.

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

**ID d’erreur :** BC42110

## <a name="to-address-this-warning"></a>Pour traiter cet avertissement

- Rendez la variable de contrôle de boucle locale en remplaçant son nom par un identificateur qui n’est pas également le nom d’un champ de la classe.

  ```vb
  For I = 1 To 10
  ```

- Précisez que la variable de contrôle de boucle est liée au champ de classe en préfixant `Me.` le nom de la variable.

  ```vb
  For Me.Index = 1 To 10
  ```

- Au lieu de vous appuyer sur l’inférence de type local, utilisez une `As` clause pour spécifier un type pour la variable de contrôle de boucle.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a> Exemple

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

- [Instruction Option Infer](../statements/option-infer-statement.md)
- [For Each...Next (instruction)](../statements/for-each-next-statement.md)
- [For...Next (instruction)](../statements/for-next-statement.md)
- [Comment : référencer l'instance actuelle d'un objet](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase et MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
