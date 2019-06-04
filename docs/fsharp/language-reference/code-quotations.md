---
title: Quotations de code
description: En savoir plus sur F# quotations de code, une fonctionnalité de langage qui vous permet de générer et utiliser des F# par programmation des expressions de code.
ms.date: 05/16/2016
ms.openlocfilehash: 5523d54a271ad1c53c6de85f37f261e0ecf6cced
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490797"
---
# <a name="code-quotations"></a>Quotations de code

> [!NOTE]
> Le lien des informations de référence sur les API pointe vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette rubrique décrit *quotations de code*, une fonctionnalité de langage qui vous permet de générer et utiliser des F# par programmation des expressions de code. Cette fonctionnalité vous permet de générer une arborescence de syntaxe abstraite qui représente F# code. L’arborescence de syntaxe abstraite peut ensuite être parcouru et traité en fonction des besoins de votre application. Par exemple, vous pouvez utiliser l’arborescence pour générer F# de code ou de générer du code dans un autre langage.

## <a name="quoted-expressions"></a>Expressions quotées

Un *expression quotée* est un F# expression dans votre code qui est délimitée de sorte qu’il n’est pas compilé dans le cadre de votre programme, mais au lieu de cela est compilé dans un objet qui représente un F# expression. Vous pouvez marquer une expression entre guillemets de deux manières : avec des informations de type ou sans informations de type. Si vous souhaitez inclure des informations de type, vous utilisez les symboles `<@` et `@>` pour délimiter l’expression entre guillemets. Si vous n’avez pas besoin d’informations de type, vous utilisez les symboles `<@@` et `@@>`. Le code suivant montre des quotations typées et non typées.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Parcourir une grande arborescence d’expression est plus rapide si vous n’incluez pas les informations de type. Le type résultant d’une expression entre guillemets avec les symboles typés est `Expr<'T>`, où le paramètre de type a le type de l’expression, comme déterminé par le F# algorithme d’inférence de type du compilateur. Lorsque vous utilisez des quotations de code sans informations de type, le type de l’expression quotée est le type non générique [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Vous pouvez appeler la [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) propriété typée `Expr` classe pour obtenir la non typé `Expr` objet.

Il existe une variété de méthodes statiques qui vous permettent de générer F# expression objets par programme dans le `Expr` classe sans utiliser les expressions quotées.

Notez qu’une quotation de code doit inclure une expression complète. Pour un `let` de liaison, par exemple, vous devez la définition du nom lié et une expression supplémentaire qui utilise la liaison. Dans la syntaxe détaillée, il s’agit d’une expression qui suit le `in` mot clé. Au niveau supérieur dans un module, il s’agit simplement l’expression suivante dans le module, mais dans une quotation, elle est explicitement requis.

Par conséquent, l’expression suivante n’est pas valide.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Mais les expressions suivantes sont valides.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

À évalue F# quotations, vous devez utiliser le [ F# évaluateur de Quotation](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Il prend en charge l’évaluation et F# objets expression.

## <a name="expr-type"></a>Type expr

Une instance de la `Expr` type représenté par un F# expression. Génériques et non génériques `Expr` types sont documentées dans le F# documentation de la bibliothèque. Pour plus d’informations, consultez [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) et [Quotations.expr, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Opérateurs d’ajout

Ajout de vous permet de combiner des quotations de code littéral avec les expressions que vous avez créés par programme ou à partir d’une autre quotation de code. Le `%` et `%%` opérateurs activent vous permet d’ajouter un F# objet d’expression dans une quotation de code. Vous utilisez le `%` opérateur pour insérer un objet expression typée dans une quotation typée ; si vous utilisez le `%%` opérateur pour insérer un objet expression non typé dans une quotation non typée. Les deux opérateurs sont des opérateurs de préfixe unaire. Par conséquent, si `expr` est une expression non typée de type `Expr`, le code suivant est valid.

```fsharp
<@@ 1 + %%expr @@>
```

Et si `expr` est une quotation typée de type `Expr<int>`, le code suivant est valid.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant illustre l’utilisation de quotations de code pour placer F# dans un objet expression de code, puis imprimer le F# code qui représente l’expression. Une fonction `println` est définie qui contient une fonction récursive `print` qui affiche un F# objet d’expression (de type `Expr`) dans un format convivial. Il existe plusieurs modèles actifs dans le [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) et [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules qui peuvent être utilisées pour analyser les objets d’expression. Cet exemple n’inclut pas tous les modèles possibles qui peuvent apparaître dans un F# expression. Un modèle non reconnu déclenche une correspondance au modèle de caractère générique (`_`) et est rendu à l’aide de la `ToString` (méthode), qui, sur le `Expr` tapez, vous permet de connaître le modèle actif à ajouter à votre expression de correspondance.

### <a name="code"></a>Code

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Sortie

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Vous pouvez également utiliser les trois modèles actifs dans le [ExprShape (module)](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) à traverser les arborescences d’expression avec moins de modèles actifs. Ces modèles actifs peuvent être utiles lorsque vous souhaitez parcourir une arborescence, mais vous n’avez pas besoin de toutes les informations dans la plupart des nœuds. Lorsque vous utilisez ces modèles, toute F# expression correspond à l’un des trois modèles suivants : `ShapeVar` si l’expression est une variable, `ShapeLambda` si l’expression est une expression lambda, ou `ShapeCombination` si l’expression n’est rien d’autre. Si vous parcourez une arborescence d’expression en utilisant les modèles actifs comme dans l’exemple de code précédent, vous devez utiliser beaucoup plus de modèles pour gérer toutes les possibles F# types d’expression et que votre code sera plus complexe. Pour plus d’informations, consultez [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination (modèle actif)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

L’exemple de code suivant peut être utilisé comme base pour les traversées plus complexes. Dans ce code, une arborescence d’expression est créée pour une expression qui implique un appel de fonction, `add`. Le [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) modèle actif est utilisé pour détecter tout appel à `add` dans l’arborescence d’expression. Ce modèle actif assigne les arguments de l’appel à la `exprList` valeur. Dans ce cas, ne Voici que deux, donc ils sont extraits et la fonction est appelée de manière récursive sur les arguments. Les résultats sont insérés dans une quotation de code qui représente un appel à `mul` à l’aide de l’opérateur de jointure (`%%`). Le `println` fonction à partir de l’exemple précédent est utilisée pour afficher les résultats.

Le code dans d’autres branches de modèle actif régénère simplement la même arborescence d’expression, donc la seule modification dans l’expression résultante est la modification à partir de `add` à `mul`.

### <a name="code"></a>Code

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Sortie

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
