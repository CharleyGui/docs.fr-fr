---
title: Définition du type anonyme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 5f6486965d9e44524420975523e10ded32a135b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755214"
---
# <a name="anonymous-type-definition-visual-basic"></a>Définition du type anonyme (Visual Basic)

En réponse à la déclaration d’une instance d’un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées pour le type.

## <a name="compiler-generated-code"></a>Code généré par le compilateur

Pour la définition suivante de `product`, le compilateur crée une nouvelle définition de classe qui contient les propriétés `Name`, `Price`, et `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

La définition de classe contient des définitions de propriété semblables à ce qui suit. Notez qu’il y a aucune `Set` méthode pour les propriétés de clé. Les valeurs des propriétés de clé sont en lecture seule.

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

En outre, les définitions de type anonymes contiennent un constructeur sans paramètre. Les constructeurs qui nécessitent des paramètres ne sont pas autorisées.

Si une déclaration de type anonyme contient au moins une propriété de clé, la définition de type substitue trois membres hérités de <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, et <xref:System.Object.ToString%2A>. Si aucune propriété de clé n’est déclarées uniquement <xref:System.Object.ToString%2A> est remplacée. Les substitutions fournissent les fonctionnalités suivantes :

- `Equals` Retourne `True` si deux instances de type anonyme sont la même instance, ou si elles répondent aux conditions suivantes :

  - Ils ont le même nombre de propriétés.

  - Les propriétés sont déclarées dans le même ordre, avec les mêmes noms et les mêmes types déduits. Les comparaisons de noms ne respectent pas la casse.

  - Au moins une des propriétés est une propriété de clé et le `Key` mot clé est appliqué aux propriétés identiques.

  - Comparaison de chaque paire correspondante des propriétés de clé retourne `True`.

    Par exemple, dans les exemples suivants, `Equals` retourne `True` uniquement pour `employee01` et `employee08`. Le commentaire précédant chaque ligne spécifie la raison pour laquelle la nouvelle instance ne correspond pas de raison `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` fournit un algorithme GetHashCode unique. L’algorithme utilise uniquement les propriétés de clé pour calculer le code de hachage.

- `ToString` Retourne une chaîne concaténée de valeurs de propriété, comme indiqué dans l’exemple suivant. La clé et les propriétés non-clé sont incluses.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Propriétés explicitement nommées d’un type anonyme ne peut pas entrer en conflit avec ces méthodes générées. Autrement dit, vous ne pouvez pas utiliser `.Equals`, `.GetHashCode`, ou `.ToString` à une propriété de nom.

Les définitions de type anonyme qui incluent au moins une propriété de clé implémentent également le <xref:System.IEquatable%601?displayProperty=nameWithType> interface, où `T` est le type du type anonyme.

> [!NOTE]
> Déclarations de types anonymes crée le même type anonyme uniquement si elles se produisent dans le même assembly, leurs propriétés ont les mêmes noms et les mêmes types déduits, les propriétés sont déclarées dans le même ordre, et les mêmes propriétés sont marquées comme propriétés de clé.

## <a name="see-also"></a>Voir aussi

- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Guide pratique pour Déduire les Types dans les déclarations de types anonymes et les noms de propriété](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
