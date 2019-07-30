---
title: Quotations de code
description: En savoir F# plus sur les Quotations de code, une fonctionnalité de langage qui vous permet F# de générer et d’utiliser des expressions de code par programmation.
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630419"
---
# <a name="code-quotations"></a>Quotations de code

> [!NOTE]
> Le lien des informations de référence sur les API pointe vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette rubrique décrit les Quotations de *code*, une fonctionnalité de langage qui vous permet de générer F# et d’utiliser des expressions de code par programmation. Cette fonctionnalité vous permet de générer une arborescence de syntaxe abstraite qui représente F# le code. L’arborescence de syntaxe abstraite peut ensuite être parcourue et traitée en fonction des besoins de votre application. Par exemple, vous pouvez utiliser l’arborescence pour générer F# du code ou générer du code dans un autre langage.

## <a name="quoted-expressions"></a>Expressions entre guillemets

Une *expression entre* guillemets F# est une expression de votre code qui est délimitée de manière à ce qu’elle ne soit pas compilée dans le cadre de votre programme, mais à la place, F# elle est compilée dans un objet qui représente une expression. Vous pouvez marquer une expression entre guillemets de l’une des deux manières suivantes: avec les informations de type ou sans informations de type. Si vous souhaitez inclure des informations de type, vous utilisez les `<@` symboles `@>` et pour délimiter l’expression entre guillemets. Si vous n’avez pas besoin d’informations de type, vous `<@@` utilisez `@@>`les symboles et. Le code suivant illustre des Quotations typées et non typées.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Parcourir une grande arborescence d’expressions est plus rapide si vous n’incluez pas d’informations de type. Le type résultant d’une expression entre guillemets avec les symboles `Expr<'T>`typés est, où le paramètre de type a le type de l’expression F# comme déterminé par l’algorithme d’inférence de type du compilateur. Quand vous utilisez des Quotations de code sans informations de type, le type de l’expression entre guillemets est le type non générique [expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Vous pouvez appeler la propriété [RAW](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) sur la classe `Expr` typée pour obtenir `Expr` l’objet non typé.

Il existe une variété de méthodes statiques qui vous permettent de F# générer des objets d’expression par programmation `Expr` dans la classe sans utiliser d’expressions entre guillemets.

Notez qu’un devis de code doit inclure une expression complète. Pour une `let` liaison, par exemple, vous avez besoin à la fois de la définition du nom lié et d’une expression supplémentaire qui utilise la liaison. En syntaxe détaillée, il s’agit d’une expression qui suit `in` le mot clé. Au niveau supérieur d’un module, il s’agit simplement de l’expression suivante dans le module, mais dans une quotation, il est explicitement requis.

Par conséquent, l’expression suivante n’est pas valide.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Toutefois, les expressions suivantes sont valides.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Pour évaluer F# des devis, vous devez utiliser l' [ F# évaluateur de quotation](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Il prend en charge l’évaluation et l' F# exécution d’objets expression.

## <a name="expr-type"></a>Expr (type)

Une instance du `Expr` type représente une F# expression. Les types génériques et non génériques `Expr` sont tous les deux documentés dans la documentation de la F# bibliothèque. Pour plus d’informations, consultez l' [espace de noms Microsoft. FSharp. Quotations](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) et [Quotations. expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Opérateurs d’épissure

L’ajout de jointures vous permet de combiner des Quotations de code littéral avec des expressions que vous avez créées par programmation ou à partir d’un autre devis de code. Les `%` opérateurs `%%` et vous permettent d’ajouter un F# objet expression à un devis de code. Vous utilisez l' `%` opérateur pour insérer un objet expression typé dans un devis typé; vous utilisez l' `%%` opérateur pour insérer un objet expression non typé dans une quotation non typée. Les deux opérateurs sont des opérateurs de préfixe unaires. Ainsi, `expr` si est une expression non typée de `Expr`type, le code suivant est valide.

```fsharp
<@@ 1 + %%expr @@>
```

Et si `expr` est une quotation typée de `Expr<int>`type, le code suivant est valide.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemples

### <a name="description"></a>Description

L’exemple suivant illustre l’utilisation de quotations de code pour placer F# du code dans un objet expression, puis imprimer F# le code qui représente l’expression. Une fonction `println` est définie et contient une fonction `print` récursive qui affiche un F# objet expression (de type `Expr`) dans un format convivial. Il existe plusieurs modèles actifs dans les modules [Microsoft. FSharp. Quotations. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) et [Microsoft. FSharp. Quotations. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) qui peuvent être utilisés pour analyser des objets expression. Cet exemple n’inclut pas tous les modèles possibles qui peuvent apparaître dans une F# expression. Tout modèle non reconnu déclenche une correspondance avec le modèle de caractère générique`_`() et est rendu à l' `ToString` aide de la méthode, qui `Expr` , sur le type, vous permet de connaître le modèle actif à ajouter à votre expression de correspondance.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Sortie

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Vous pouvez également utiliser les trois modèles actifs dans le [module ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) pour parcourir les arborescences d’expressions avec moins de modèles actifs. Ces modèles actifs peuvent être utiles lorsque vous souhaitez parcourir une arborescence, mais que vous n’avez pas besoin de toutes les informations de la plupart des nœuds. Lorsque vous utilisez ces modèles, toute F# expression correspond à l’un des trois modèles suivants `ShapeVar` : si l’expression est une variable `ShapeLambda` , si l’expression est une expression lambda ou `ShapeCombination` si l’expression est autre chose. Si vous parcourez une arborescence d’expressions en utilisant les modèles actifs comme dans l’exemple de code précédent, vous devez utiliser beaucoup plus de modèles pour F# gérer tous les types d’expressions possibles, et votre code sera plus complexe. Pour plus d’informations, consultez [ExprShape.&#124;ShapeVar&#124;ShapeLambda ShapeCombination active pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

L’exemple de code suivant peut être utilisé comme base pour des parcours plus complexes. Dans ce code, une arborescence de l’expression est créée pour une expression qui implique un appel `add`de fonction,. Le modèle actif [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) est utilisé pour détecter tout appel à `add` dans l’arborescence de l’expression. Ce modèle actif assigne les arguments de l’appel à la `exprList` valeur. Dans ce cas, il n’y en a que deux, donc elles sont extraites et la fonction est appelée de manière récursive sur les arguments. Les résultats sont insérés dans un quotation de code qui représente un `mul` appel à à l’aide de l'`%%`opérateur Splice (). La `println` fonction de l’exemple précédent est utilisée pour afficher les résultats.

Le code dans les autres branches de modèles actifs régénère simplement la même arborescence d’expressions, donc la seule modification dans l’expression résultante est la `add` modification `mul`de à.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Sortie

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
