---
title: Définition du type anonyme
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404899"
---
# <a name="anonymous-type-definition-visual-basic"></a>Définition du type anonyme (Visual Basic)

En réponse à la déclaration d’une instance d’un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées pour le type.

## <a name="compiler-generated-code"></a>Code généré par le compilateur

Pour la définition suivante de `product` , le compilateur crée une nouvelle définition de classe qui contient les propriétés `Name` , `Price` et `OnHand` .

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

La définition de classe contient des définitions de propriétés semblables à ce qui suit. Notez qu’il n’existe aucune `Set` méthode pour les propriétés de clé. Les valeurs des propriétés de clé sont en lecture seule.

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

En outre, les définitions de type anonyme contiennent un constructeur sans paramètre. Les constructeurs qui requièrent des paramètres ne sont pas autorisés.

Si une déclaration de type anonyme contient au moins une propriété de clé, la définition de type remplace trois membres hérités de <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A> . Si aucune propriété de clé n’est déclarée, seul <xref:System.Object.ToString%2A> est substitué. Les remplacements offrent les fonctionnalités suivantes :

- `Equals`retourne `True` si deux instances de type anonyme sont la même instance ou si elles remplissent les conditions suivantes :

  - Ils ont le même nombre de propriétés.

  - Les propriétés sont déclarées dans le même ordre, avec les mêmes noms et les mêmes types déduits. Les comparaisons de noms ne respectent pas la casse.

  - Au moins une des propriétés est une propriété de clé et le `Key` mot clé est appliqué aux mêmes propriétés.

  - La comparaison de chaque paire correspondante de propriétés de clé retourne `True` .

    Par exemple, dans les exemples suivants, `Equals` retourne `True` uniquement pour `employee01` et `employee08` . Le commentaire avant chaque ligne spécifie la raison pour laquelle la nouvelle instance ne correspond pas `employee01` .

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode`fournit un algorithme GetHashCode unique approprié. L’algorithme utilise uniquement les propriétés de clé pour calculer le code de hachage.

- `ToString`retourne une chaîne de valeurs de propriété concaténées, comme indiqué dans l’exemple suivant. Les propriétés clés et non-clés sont incluses.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Les propriétés explicitement nommées d’un type anonyme ne peuvent pas entrer en conflit avec ces méthodes générées. Autrement dit, vous ne pouvez pas utiliser `.Equals` , `.GetHashCode` ou `.ToString` pour nommer une propriété.

Les définitions de types anonymes qui incluent au moins une propriété de clé implémentent également l' <xref:System.IEquatable%601?displayProperty=nameWithType> interface, où `T` est le type du type anonyme.

> [!NOTE]
> Les déclarations de type anonyme créent le même type anonyme uniquement si elles se produisent dans le même assembly, si leurs propriétés ont les mêmes noms et les mêmes types déduits, les propriétés sont déclarées dans le même ordre et les mêmes propriétés sont marquées comme propriétés de clé.

## <a name="see-also"></a>Voir aussi

- [Types anonymes](anonymous-types.md)
- [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
