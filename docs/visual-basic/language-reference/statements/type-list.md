---
title: Type List
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412986"
---
# <a name="type-list-visual-basic"></a>Liste de types (Visual Basic)

Spécifie les *paramètres de type* pour un élément de programmation *générique* . Plusieurs paramètres sont séparés par des virgules. Voici la syntaxe d’un paramètre de type.

## <a name="syntax"></a>Syntaxe

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`genericmodifier`|Facultatif. Peut être utilisé uniquement dans les interfaces et les délégués génériques. Vous pouvez déclarer un covariant de type à l’aide du mot clé [out](../modifiers/out-generic-modifier.md) ou de contravariant à l’aide du mot clé [in](../modifiers/in-generic-modifier.md) . Consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).|
|`typename`|Obligatoire. Nom du paramètre de type. Il s’agit d’un espace réservé, à remplacer par un type défini fourni par l’argument de type correspondant.|
|`constraintlist`|Facultatif. Liste des exigences qui contraignent le type de données qui peut être fourni pour `typename` . Si vous avez plusieurs contraintes, mettez-les entre accolades ( `{ }` ) et séparez-les par des virgules. Vous devez introduire la liste de contraintes avec le mot clé [As](as-clause.md) . Vous ne devez utiliser `As` qu’une seule fois, au début de la liste.|

## <a name="remarks"></a>Notes

Chaque élément de programmation générique doit accepter au moins un paramètre de type. Un paramètre de type est un espace réservé pour un type spécifique (un *élément construit*) que le code client spécifie lorsqu’il crée une instance du type générique. Vous pouvez définir une classe, une structure, une interface, une procédure ou un délégué générique.

Pour plus d’informations sur la définition d’un type générique, consultez [types génériques dans Visual Basic](../../programming-guide/language-features/data-types/generic-types.md). Pour plus d’informations sur les noms de paramètres de type, consultez [noms d’éléments déclarés](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="rules"></a>Règles

- **Parenthèses.** Si vous fournissez une liste de paramètres de type, vous devez la placer entre parenthèses, et vous devez introduire la liste avec le mot clé [of](of-clause.md) . Vous ne devez utiliser `Of` qu’une seule fois, au début de la liste.

- **Contraintes.** Une liste de *contraintes* sur un paramètre de type peut inclure les éléments suivants dans n’importe quelle combinaison :

  - N’importe quel nombre d’interfaces. Le type fourni doit implémenter chaque interface dans cette liste.

  - Au plus une classe. Le type fourni doit hériter de cette classe.

  - Mot clé `New`. Le type fourni doit exposer un constructeur sans paramètre auquel votre type générique peut accéder. Cela est utile si vous limitez un paramètre de type par une ou plusieurs interfaces. Un type qui implémente des interfaces n’expose pas nécessairement un constructeur et, selon le niveau d’accès d’un constructeur, le code dans le type générique peut ne pas être en mesure d’y accéder.

  - Le `Class` mot clé ou le `Structure` mot clé. Le `Class` mot clé contraindre un paramètre de type générique à exiger que tout argument de type soit passé comme type de référence, par exemple une chaîne, un tableau ou un délégué, ou un objet créé à partir d’une classe. Le `Structure` mot clé limite un paramètre de type générique pour exiger que tout argument de type qui lui est passé soit un type valeur, par exemple une structure, une énumération ou un type de données élémentaire. Vous ne pouvez pas `Class` inclure `Structure` à la fois et dans le même `constraintlist` .

  Le type fourni doit satisfaire à toutes les exigences que vous incluez dans `constraintlist` .

  Les contraintes sur chaque paramètre de type sont indépendantes des contraintes sur d’autres paramètres de type.

## <a name="behavior"></a>Comportement

- **Substitution au moment de la compilation.** Lorsque vous créez un type construit à partir d’un élément de programmation générique, vous fournissez un type défini pour chaque paramètre de type. Le compilateur Visual Basic remplace ce type fourni pour chaque occurrence de `typename` dans l’élément générique.

- **Absence de contraintes.** Si vous ne spécifiez pas de contraintes sur un paramètre de type, votre code est limité aux opérations et aux membres pris en charge par le [type de données objet](../data-types/object-data-type.md) pour ce paramètre de type.

## <a name="example"></a>Exemple

L’exemple suivant montre une définition squelette d’une classe Dictionary générique, y compris une fonction squelette pour ajouter une nouvelle entrée au dictionnaire.

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>Exemple

Étant donné que `dictionary` est générique, le code qui l’utilise peut créer divers objets à partir de celui-ci, chacun ayant les mêmes fonctionnalités, mais agissant sur un type de données différent. L’exemple suivant montre une ligne de code qui crée un `dictionary` objet avec des `String` entrées et des `Integer` clés.

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>Exemple

L’exemple suivant illustre la définition de squelette équivalente générée par l’exemple précédent.

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Of](of-clause.md)
- [Nouvel opérateur](../operators/new-operator.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Object Data Type](../data-types/object-data-type.md)
- [Function (instruction)](function-statement.md)
- [Structure, instruction](structure-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Procédure : Utiliser une classe générique](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Dans](../modifiers/in-generic-modifier.md)
- [À](../modifiers/out-generic-modifier.md)
