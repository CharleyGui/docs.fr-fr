---
title: Quotations de code
description: 'En savoir plus sur les Quotations de code F #, une fonctionnalité de langage qui vous permet de générer et d’utiliser des expressions de code F # par programmation.'
ms.date: 05/16/2016
ms.openlocfilehash: bb5c03edd180c42667731bb90d7a1f624ed2e522
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855390"
---
# <a name="code-quotations"></a>Quotations de code

Cet article décrit les *Quotations de code*, une fonctionnalité de langage qui vous permet de générer et d’utiliser des expressions de code F # par programmation. Cette fonctionnalité vous permet de générer une arborescence de syntaxe abstraite qui représente le code F #. L’arborescence de syntaxe abstraite peut ensuite être parcourue et traitée en fonction des besoins de votre application. Par exemple, vous pouvez utiliser l’arborescence pour générer du code F # ou générer du code dans un autre langage.

> [!NOTE]
> La référence de l’API docs.microsoft.com pour F # n’est pas terminée. Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="quoted-expressions"></a>Expressions entre guillemets

Une *expression entre guillemets* est une expression f # dans votre code qui est délimitée de telle façon qu’elle n’est pas compilée dans le cadre de votre programme, mais à la place, elle est compilée dans un objet qui représente une expression F #. Vous pouvez marquer une expression entre guillemets de l’une des deux manières suivantes : avec les informations de type ou sans informations de type. Si vous souhaitez inclure des informations de type, vous utilisez les symboles `<@` et `@>` pour délimiter l’expression entre guillemets. Si vous n’avez pas besoin d’informations de type, vous utilisez les symboles `<@@` et `@@>` . Le code suivant illustre des Quotations typées et non typées.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Parcourir une grande arborescence d’expressions est plus rapide si vous n’incluez pas d’informations de type. Le type résultant d’une expression entre guillemets avec les symboles typés est `Expr<'T>` , où le paramètre de type a le type de l’expression tel que déterminé par l’algorithme d’inférence de type du compilateur F #. Quand vous utilisez des Quotations de code sans informations de type, le type de l’expression entre guillemets est le type non générique [expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Vous pouvez appeler la propriété [RAW](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) sur la classe typée `Expr` pour obtenir l’objet non typé `Expr` .

Il existe une variété de méthodes statiques qui vous permettent de générer des objets d’expression F # par programmation dans la `Expr` classe sans utiliser d’expressions entre guillemets.

Notez qu’un devis de code doit inclure une expression complète. Pour une `let` liaison, par exemple, vous avez besoin à la fois de la définition du nom lié et d’une expression supplémentaire qui utilise la liaison. En syntaxe détaillée, il s’agit d’une expression qui suit le `in` mot clé. Au niveau supérieur d’un module, il s’agit simplement de l’expression suivante dans le module, mais dans une quotation, il est explicitement requis.

Par conséquent, l’expression suivante n’est pas valide.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Toutefois, les expressions suivantes sont valides.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Pour évaluer les guillemets F #, vous devez utiliser l' [évaluateur de guillemets f #](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Il prend en charge l’évaluation et l’exécution des objets d’expression F #.

## <a name="expr-type"></a>Expr (type)

Une instance du `Expr` type représente une expression F #. Les types génériques et non génériques `Expr` sont décrits dans la documentation de la bibliothèque F #. Pour plus d’informations, consultez l' [espace de noms Microsoft. FSharp. Quotations](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) et [Quotations. expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Opérateurs d’épissure

L’ajout de jointures vous permet de combiner des Quotations de code littéral avec des expressions que vous avez créées par programmation ou à partir d’un autre devis de code. Les `%` `%%` opérateurs et vous permettent d’ajouter un objet d’expression F # dans une quotation de code. Vous utilisez l' `%` opérateur pour insérer un objet expression typé dans un devis typé ; vous utilisez l' `%%` opérateur pour insérer un objet expression non typé dans une quotation non typée. Les deux opérateurs sont des opérateurs de préfixe unaires. Ainsi `expr` , si est une expression non typée de type `Expr` , le code suivant est valide.

```fsharp
<@@ 1 + %%expr @@>
```

Et si `expr` est une quotation typée de type `Expr<int>` , le code suivant est valide.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant illustre l’utilisation de quotations de code pour placer du code F # dans un objet expression, puis imprimer le code F # qui représente l’expression. Une fonction `println` est définie et contient une fonction récursive `print` qui affiche un objet d’expression F # (de type `Expr` ) dans un format convivial. Il existe plusieurs modèles actifs dans les modules [Microsoft. FSharp. Quotations. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) et [Microsoft. FSharp. Quotations. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) qui peuvent être utilisés pour analyser des objets expression. Cet exemple n’inclut pas tous les modèles possibles qui peuvent apparaître dans une expression F #. Tout modèle non reconnu déclenche une correspondance avec le modèle de caractère générique ( `_` ) et est rendu à l’aide de la `ToString` méthode, qui, sur le `Expr` type, vous permet de connaître le modèle actif à ajouter à votre expression de correspondance.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Output

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Vous pouvez également utiliser les trois modèles actifs dans le [module ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) pour parcourir les arborescences d’expressions avec moins de modèles actifs. Ces modèles actifs peuvent être utiles lorsque vous souhaitez parcourir une arborescence, mais que vous n’avez pas besoin de toutes les informations de la plupart des nœuds. Lorsque vous utilisez ces modèles, toute expression F # correspond à l’un des trois modèles suivants : `ShapeVar` si l’expression est une variable, `ShapeLambda` si l’expression est une expression lambda, ou `ShapeCombination` si l’expression est autre chose. Si vous parcourez une arborescence d’expressions en utilisant les modèles actifs comme dans l’exemple de code précédent, vous devez utiliser beaucoup plus de modèles pour gérer tous les types d’expression F # possibles, et votre code sera plus complexe. Pour plus d’informations, consultez [ExprShape. ShapeVar&#124;ShapeLambda&#124;ShapeCombination modèle actif](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

L’exemple de code suivant peut être utilisé comme base pour des parcours plus complexes. Dans ce code, une arborescence de l’expression est créée pour une expression qui implique un appel de fonction, `add` . Le modèle actif [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) est utilisé pour détecter tout appel à `add` dans l’arborescence de l’expression. Ce modèle actif assigne les arguments de l’appel à la `exprList` valeur. Dans ce cas, il n’y en a que deux, donc elles sont extraites et la fonction est appelée de manière récursive sur les arguments. Les résultats sont insérés dans un quotation de code qui représente un appel à à `mul` l’aide de l’opérateur Splice ( `%%` ). La `println` fonction de l’exemple précédent est utilisée pour afficher les résultats.

Le code dans les autres branches de modèles actifs régénère simplement la même arborescence d’expressions, donc la seule modification dans l’expression résultante est la modification de `add` à `mul` .

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Output

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
