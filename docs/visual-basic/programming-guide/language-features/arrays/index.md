---
title: Tableaux dans Visual Basic
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 12846b80f04e9fa6d1188485ad55b061cd2863fa
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758849"
---
# <a name="arrays-in-visual-basic"></a>Tableaux dans Visual Basic

Un tableau est un ensemble de valeurs appelées *éléments*, qui sont liés logiquement entre eux. Par exemple, un tableau peut contenir le nombre d’étudiants de chaque niveau scolaire dans une école primaire ; chaque élément du tableau est le nombre d’étudiants dans une classe unique. De même, un tableau peut se composer de notes d’un étudiant pour une classe ; chaque élément du tableau est un niveau unique.

Il est possible de variables individuelles à stocker chaque notre d’éléments de données. Par exemple, si notre application analyse les notes des étudiants, nous pouvons utiliser une variable distincte pour chaque note de l’étudiant, tel que `englishGrade1`, `englishGrade2`, etc. Cette approche présente trois principales limitations :

- Nous devons savoir au moment du design exactement le nombre de notes que nous devons gérer.
- Gérer un grand nombre de qualités rapidement devient difficile à gérer. Cela facilite ensuite une application beaucoup plus susceptible d’avoir des bogues sérieux.
- Il est difficile à gérer. Chaque nouveau grade que nous apportons nécessite que l’application est modifiée, recompilée et redéployée.

En utilisant un tableau, vous pouvez faire référence à ces valeurs connexes par le même nom et utiliser un nombre qui est appelé un *index* ou *indice* pour identifier un élément individuel en fonction de sa position dans le tableau. Les index d’un tableau vont de 0 à un de moins que le nombre total d’éléments dans le tableau. Lorsque vous utilisez la syntaxe Visual Basic pour définir la taille d’un tableau, vous spécifiez ses index le plus élevé, pas le nombre total d’éléments dans le tableau. Vous pouvez utiliser le tableau en tant qu’unité, et la possibilité d’itérer au sein de ses éléments vous évite d’avoir à connaître exactement le nombre d’éléments qu’il contient au moment du design.

Voici quelques exemples sommaires avant d’entrer dans les détails :

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>Éléments de tableau dans un tableau simple

Nous allons créer un tableau nommé `students` pour stocker le nombre d’étudiants de chaque niveau scolaire dans une école primaire. Les index des éléments s’échelonnent de 0 à 6. À l’aide de ce tableau est plus simple que de déclarer sept variables.

L’illustration suivante montre le `students` tableau. Pour chaque élément du tableau :

- L’index de l’élément représente le niveau scolaire (l’index 0 représente le niveau maternelle).

- La valeur contenue dans l’élément représente le nombre d’élèves de cette catégorie.

![Diagramme montrant un tableau des nombres d’étudiants](./media/index/students-array-elements.gif)

L’exemple suivant contient le code Visual Basic qui crée et utilise le tableau :

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

L’exemple effectue trois opérations :

- Elle déclare un `students` tableau avec sept éléments. Le nombre `6` dans le tableau de déclaration indique au dernier index dans le tableau ; il l’est inférieur au nombre d’éléments dans le tableau.
- Il assigne des valeurs à chaque élément du tableau. Éléments de tableau sont accessibles en utilisant le nom de tableau et en incluant l’index de l’élément individuel entre parenthèses.
- Il répertorie chaque valeur du tableau. L’exemple utilise un [ `For` ](../../../language-reference/statements/for-next-statement.md) instruction d’accéder à chaque élément du tableau par son numéro d’index.

Le `students` tableau dans l’exemple précédent est un tableau unidimensionnel, car elle utilise un seul index. Un tableau qui utilise plusieurs index ou indices est appelé *multidimensionnelles*. Pour plus d’informations, consultez le reste de cet article et [Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md).

## <a name="creating-an-array"></a>Création d’un tableau

Vous pouvez définir la taille d’un tableau de plusieurs façons :

- Vous pouvez spécifier la taille lorsque le tableau est déclaré :

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- Vous pouvez utiliser un `New` clause pour indiquer la taille d’un tableau lors de sa création :

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

Si vous avez un tableau existant, vous pouvez redéfinir sa taille à l’aide de la [ `ReDim` ](../../../language-reference/statements/redim-statement.md) instruction. Vous pouvez spécifier que le `ReDim` instruction conserver les valeurs qui se trouvent dans le tableau, ou vous pouvez spécifier qu’elle crée un tableau vide. L’exemple suivant montre les différentes utilisations possibles de l’instruction `ReDim` pour modifier la taille d’un tableau existant.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

Pour plus d’informations, consultez le [instruction ReDim](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Stockage de valeurs dans un tableau

Vous pouvez accéder à chaque emplacement d’un tableau en utilisant un index de type `Integer`. Vous pouvez stocker des valeurs dans un tableau et les récupérer par la suite en référençant chaque emplacement du tableau en utilisant son index entre parenthèses. Index pour les tableaux multidimensionnels sont séparés par des virgules (,). Vous avez besoin d’un index pour chaque dimension de tableau.

L’exemple suivant montre quelques instructions qui stockent et récupèrent des valeurs dans des tableaux.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Remplissage d’un tableau avec des littéraux de tableau

En utilisant un littéral de tableau, vous pouvez remplir un tableau avec un ensemble initial de valeurs en même temps que vous la créez. Un littéral de tableau se compose d’une liste de valeurs séparées par des virgules mise entre accolades (`{}`).

Quand vous créez un tableau en utilisant un littéral de tableau, vous pouvez soit indiquer le type du tableau, soit utiliser l’inférence de type pour déterminer le type du tableau. L’exemple suivant montre les deux options.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

Lorsque vous utilisez l’inférence de type, le type du tableau est déterminé par le *type dominant* dans la liste des valeurs littérales. Le type dominant est le type vers lequel tous les autres types dans le tableau peuvent s’étendre. Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types du tableau peuvent se réduire. Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`. Par exemple, si la liste de valeurs fournie au littéral de tableau contient des valeurs de type `Integer`, `Long`et `Double`, le tableau qui en résulte est de type `Double`. Étant donné que `Integer` et `Long` s’étendent seulement à `Double`, `Double` est le type dominant. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> Vous pouvez utiliser l’inférence de type uniquement pour les tableaux qui sont définies comme des variables locales dans un membre de type. Si une définition de type explicite est absente, tableaux définis avec des littéraux de tableau au niveau de la classe sont de type `Object[]`. Pour plus d’informations, consultez [inférence de type Local](../variables/local-type-inference.md).

Notez que l’exemple précédent définit `values` sous forme de tableau de type `Double` même si les littéraux de tableau sont de type `Integer`. Vous pouvez créer ce tableau, car les valeurs du littéral de tableau peuvent s’étendre `Double` valeurs.

Vous pouvez également créer et remplir un tableau multidimensionnel à l’aide de *imbriqués des littéraux de tableau*. Littéraux de tableau imbriqués doivent avoir un nombre de dimensions qui est cohérent avec le tableau obtenu. L’exemple suivant crée un tableau à deux dimensions d’entiers à l’aide de littéraux de tableau imbriqués.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

Lorsque vous utilisez des littéraux de tableau imbriqués pour créer et remplir un tableau, une erreur se produit si le nombre d’éléments dans les littéraux de tableau imbriqué ne correspondre pas. Une erreur se produit également si vous déclarez explicitement la variable de tableau pour avoir un nombre différent de dimensions que les littéraux de tableau.

Comme pour les tableaux unidimensionnels, vous pouvez compter sur l’inférence de type lors de la création d’un tableau multidimensionnel avec des littéraux de tableau imbriqué. Le type déduit est le type dominant pour toutes les valeurs dans les littéraux de tableau pour le niveau d’imbrication. L’exemple suivant crée un tableau à deux dimensions de type `Double[,]` à partir des valeurs qui sont de type `Integer` et `Double`.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Pour obtenir des exemples supplémentaires, consultez [Comment : Initialiser une Variable tableau en Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Itération au sein d’un tableau

Lorsque vous parcourez un tableau, vous accédez à chaque élément dans le tableau à partir de l’index la plus basse à la plus élevée ou la plus élevée à la plus basse. En règle générale, utilisez le [pour... L’instruction suivante](../../../language-reference/statements/for-next-statement.md) ou [pour chaque... L’instruction suivante](../../../language-reference/statements/for-each-next-statement.md) pour itérer les éléments d’un tableau. Lorsque vous ne connaissez pas les limites supérieures du tableau, vous pouvez appeler la <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> méthode pour obtenir la valeur la plus élevée de l’index. Bien que la valeur d’index la plus basse est presque toujours 0, vous pouvez appeler la <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> méthode pour obtenir la valeur la plus basse de l’index.

L’exemple suivant effectue une itération dans un tableau unidimensionnel à l’aide de la [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) instruction.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

L’exemple suivant effectue une itération dans un tableau multidimensionnel en utilisant un [ `For...Next` ](../../../language-reference/statements/for-next-statement.md) instruction. La méthode <xref:System.Array.GetUpperBound%2A> dispose d’un paramètre qui spécifie la dimension. `GetUpperBound(0)` Retourne l’index le plus élevé de la première dimension et `GetUpperBound(1)` retourne l’index le plus élevé de la deuxième dimension.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

L’exemple suivant utilise un [For Each... L’instruction suivante](../../../language-reference/statements/for-each-next-statement.md)pour itérer un tableau unidimensionnel et un tableau à deux dimensions.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Taille du tableau

La taille d’un tableau est le produit des longueurs de toutes ses dimensions. Elle représente le nombre total d’éléments actuellement contenus dans le tableau.  Par exemple, l’exemple suivant déclare un tableau 2D avec quatre éléments dans chaque dimension. Comme le montre la sortie de l’exemple, les taille du tableau sont 16 (ou (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> Cette discussion de la taille du tableau ne s’applique pas aux tableaux en escalier. Pour plus d’informations sur les tableaux en escalier et déterminer la taille d’un tableau en escalier, consultez le [tableaux en escalier](#jagged-arrays) section.

Vous pouvez trouver la taille d’un tableau en utilisant la propriété <xref:System.Array.Length%2A?displayProperty=nameWithType>. Vous pouvez trouver la longueur de chaque dimension d’un tableau multidimensionnel à l’aide de la <xref:System.Array.GetLength%2A?displayProperty=nameWithType> (méthode).

Vous pouvez redimensionner une variable tableau en assignant un nouvel objet tableau ou en utilisant le [ `ReDim` instruction](../../../language-reference/statements/redim-statement.md) instruction. L’exemple suivant utilise la `ReDim` instruction pour passer un tableau de 100 éléments à un tableau 51-élément.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Il y a plusieurs points à prendre en compte en ce qui concerne la taille d’un tableau.

|||
|---|---|
|Longueur de dimension|L’index de chaque dimension est basé sur 0, ce qui signifie qu’il varie de 0 à sa limite supérieure. Par conséquent, la longueur d’une dimension donnée est supérieure à la limite supérieure déclarée de cette dimension.|
|Limites de longueur|La longueur de chaque dimension d’un tableau est limitée à la valeur maximale de la `Integer` type de données, qui est <xref:System.Int32.MaxValue?displayProperty=nameWithType> ou (2 ^ 31) - 1. Cependant, la taille totale d’un tableau est aussi limitée par la mémoire disponible sur votre système. Si vous essayez d’initialiser un tableau qui dépasse la quantité de mémoire disponible, le runtime lève une <xref:System.OutOfMemoryException>.|
|Taille et taille d’élément|La taille d’un tableau est indépendante du type de données de ses éléments. La taille représente toujours le nombre total d’éléments, pas le nombre d’octets qu’ils occupent dans la mémoire.|
|Consommation de mémoire|Il est déconseillé de faire des hypothèses sur la façon dont un tableau est stocké en mémoire. Le stockage varie selon la largeur de données de la plateforme. Par exemple, un même tableau utilise plus de mémoire sur un système 64 bits que sur un système 32 bits. Selon la configuration du système au moment de l’initialisation d’un tableau, le Common Language Runtime (CLR) peut assigner du stockage de façon à regrouper les éléments aussi près que possible les uns des autres ou pour tous les adapter aux limites matérielles naturelles. De même, un tableau nécessite un supplément de stockage pour ses informations de contrôle, un supplément qui augmente d’autant à chaque dimension ajoutée.|

## <a name="the-array-type"></a>Le type de tableau

Chaque tableau a un type de données, ce qui est différent du type de données de ses éléments. Le type de données varie d’un tableau à un autre. En effet, le type de données d’un tableau est déterminé par le nombre de dimensions (ou *rang*) qu’il possède et par le type de données de ses éléments. Deux variables tableau sont des mêmes données, tapez uniquement si elles ont le même rang et leurs éléments ont les mêmes données de type. Les longueurs des dimensions d’un tableau n’influencent pas le type de données de tableau.

Chaque tableau hérite de la classe <xref:System.Array?displayProperty=nameWithType> et vous pouvez déclarer une variable de type `Array`, mais vous ne pouvez pas créer un tableau de type `Array`. Par exemple, bien que le code suivant déclare le `arr` variable comme étant de type `Array` et appelle le <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> méthode pour instancier le tableau, le type du tableau s’avère Object [].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

De même, [l’instruction ReDim](../../../language-reference/statements/redim-statement.md) ne peut pas opérer sur une variable déclarée comme étant du type `Array`. Pour ces raisons et pour la sécurité de type, il est recommandé de déclarer chaque tableau comme un type spécifique.

Vous pouvez déterminer le type de données d’un tableau ou de ses éléments de plusieurs façons.

- Vous pouvez appeler la <xref:System.Object.GetType%2A> méthode sur la variable pour obtenir un <xref:System.Type> objet qui représente le type au moment de l’exécution de la variable. L’objet <xref:System.Type> contient des informations complètes dans ses propriétés et méthodes.
- Vous pouvez passer la variable à la <xref:Microsoft.VisualBasic.Information.TypeName%2A> fonction pour obtenir un `String` avec le nom de type au moment de l’exécution.

L’exemple suivant appelle les deux valeurs le `GetType` (méthode) et le `TypeName` fonction permettant de déterminer le type d’un tableau. Le type de tableau est `Byte(,)`. Notez que le <xref:System.Type.BaseType%2A?displayProperty=nameWithType> propriété indique également que le type de base du tableau d’octets est la <xref:System.Array> classe.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Tableaux en tant que valeurs de retour et paramètres

Pour retourner un tableau à partir d’une procédure `Function`, spécifiez le type de données du tableau et le nombre de dimensions en tant que type de retour de [l’instruction Function](../../../language-reference/statements/function-statement.md). Dans la fonction, déclarez une variable tableau locale avec le même type de données et le même nombre de dimensions. Dans [l’instruction Return](../../../language-reference/statements/return-statement.md), incluez la variable tableau locale sans parenthèses.

Pour spécifier un tableau en tant que paramètre d’une procédure `Sub` ou `Function` , définissez le paramètre en tant que tableau avec un type de données et un nombre de dimensions spécifiés. Dans l’appel à la procédure, passez une variable de tableau avec le même type de données et le nombre de dimensions.

Dans l’exemple suivant, le `GetNumbers` fonction renvoie une `Integer()`, un tableau unidimensionnel de type `Integer`. La procédure `ShowNumbers` accepte un argument `Integer()` .

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

Dans l’exemple suivant, le `GetNumbersMultiDim` fonction renvoie une `Integer(,)`, un tableau à deux dimensions de type `Integer`.  La procédure `ShowNumbersMultiDim` accepte un argument `Integer(,)` .

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Tableaux en escalier

Parfois, la structure de données de votre application est à deux dimensions, mais pas rectangulaire. Par exemple, vous pouvez utiliser un tableau pour stocker les données relatives à la température maximale de chaque jour du mois. La première dimension du tableau représente le mois, mais la deuxième dimension représente le nombre de jours, et le nombre de jours dans un mois n’est pas uniform. Un *tableau en escalier*, qui est également appelée un *tableau de tableaux*, est conçu pour de tels scénarios. Un tableau en escalier est un tableau dont les éléments sont également des tableaux. Un tableau en escalier et chaque élément qu’il contient peut avoir une ou plusieurs dimensions.

L’exemple suivant utilise un tableau de mois, dont chaque élément est un tableau de jours. L’exemple utilise un tableau en escalier, car les différents mois ont le même nombre de jours.  L’exemple montre comment créer un tableau en escalier, affecter des valeurs et récupérer et afficher ses valeurs.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

L’exemple précédent assigne des valeurs dans le tableau en escalier sur une base de l’élément par élément en utilisant un `For...Next` boucle. Vous pouvez également affecter des valeurs aux éléments d’un tableau en escalier à l’aide de littéraux de tableau imbriqués. Toutefois, la tentative d’utilisation imbriquée littéraux de tableaux (par exemple, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) génère l’erreur du compilateur [BC30568](../../../,,/../misc/bc30568.md). Pour corriger cette erreur, placez les littéraux de tableau internes entre parenthèses. Les parenthèses forcent l’expression de littéral de tableau doit être évaluée, et les valeurs résultantes sont utilisés avec le littéral de tableau externe, comme le montre l’exemple suivant.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

Un tableau en escalier est un tableau unidimensionnel dont les éléments contiennent des tableaux. Par conséquent, le <xref:System.Array.Length%2A?displayProperty=nameWithType> propriété et la `Array.GetLength(0)` méthode retourne le nombre d’éléments dans le tableau unidimensionnel, et `Array.GetLength(1)` lève un <xref:System.IndexOutOfRangeException> , car un tableau en escalier n’est pas multidimensionnel. Vous déterminez le nombre d’éléments dans chaque sous-tableau en récupérant la valeur du chaque sous-tableau <xref:System.Array.Length%2A?displayProperty=nameWithType> propriété. L’exemple suivant illustre comment déterminer le nombre d’éléments dans un tableau en escalier.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Tableaux de longueur zéro

Visual Basic fait la distinction entre un tableau non initialisé (un tableau dont la valeur est `Nothing`) et un *tableau de longueur zéro* ou tableau vide (un tableau qui ne comporte aucun élément.) Un tableau non initialisé est celui qui n’a pas été dimensionnée ou avaient toutes les valeurs affectées à ce dernier. Exemple :

```vb
Dim arr() As String
```

Un tableau de longueur nulle est déclaré avec une dimension de -1. Exemple :

```vb
Dim arrZ(-1) As String
```

Vous pouvez être amené à créer un tableau de longueur zéro dans les cas suivants :

- Sans risquer une <xref:System.NullReferenceException> exception, votre code doit accéder aux membres de la <xref:System.Array> classe, telle que <xref:System.Array.Length%2A> ou <xref:System.Array.Rank%2A>, ou appeler une fonction Visual Basic comme <xref:Microsoft.VisualBasic.Information.UBound%2A>.

- Vous souhaitez simplifier votre code sans avoir à vérifier pour `Nothing` comme un cas particulier.

- Votre code interagit avec une interface de programmation d’applications (API) qui vous oblige à passer un tableau de longueur zéro à une ou plusieurs procédures ou qui retourne un tableau de longueur zéro à partir d’une ou plusieurs procédures.

## <a name="splitting-an-array"></a>Fractionnement d’un tableau

Dans certains cas, vous devrez peut-être fractionner un tableau unique en plusieurs tableaux. Cela implique identifiant l’ou les points à laquelle le tableau doit être fractionné et cracher ensuite le tableau en deux ou plusieurs tableaux distincts.

> [!NOTE]
> Cette section ne traite pas le fractionnement d’une chaîne unique dans un tableau de chaînes en fonction de certains délimiteur. Pour plus d’informations sur le fractionnement d’une chaîne, consultez la <xref:System.String.Split%2A?displayProperty=nameWithType> (méthode).

Les critères les plus courants pour fractionner un tableau sont :

- Nombre d’éléments dans le tableau. Par exemple, vous souhaiterez peut-être fractionner un tableau de plus d’un nombre spécifié d’éléments en un nombre de parties approximativement égales. Pour cela, vous pouvez utiliser la valeur retournée à l’aide du <xref:System.Array.Length%2A?displayProperty=nameWithType> ou <xref:System.Array.GetLength%2A?displayProperty=nameWithType> (méthode).

- La valeur d’un élément, qui sert d’un délimiteur qui indique où le tableau doit être fractionné. Vous pouvez rechercher une valeur spécifique en appelant le <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> et <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> méthodes.

Une fois que vous avez déterminé l’ou les index à laquelle le tableau doit être fractionné, vous pouvez ensuite créer les tableaux individuels en appelant le <xref:System.Array.Copy%2A?displayProperty=nameWithType> (méthode).

L’exemple suivant fractionne un tableau en deux tableaux d’environ de taille égale. (Si le nombre total d’éléments de tableau est impair, le premier tableau a un élément de plus que la seconde).

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

L’exemple suivant fractionne un tableau de chaînes en deux tableaux en fonction de la présence d’un élément dont la valeur est « zzz », qui sert le délimiteur de tableau. Les nouvelles baies n’incluent pas l’élément qui contient le délimiteur.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Jointure de tableaux

Vous pouvez également combiner un nombre de groupes dans un seul tableau plus grand. Pour ce faire, vous utilisez également le <xref:System.Array.Copy%2A?displayProperty=nameWithType> (méthode).

> [!NOTE]
> Cette section ne traite pas de joindre un tableau de chaînes en une seule chaîne. Pour plus d’informations sur la jonction d’un tableau de chaînes, consultez le <xref:System.String.Join%2A?displayProperty=nameWithType> (méthode).

Avant de copier les éléments de chaque tableau dans le nouveau tableau, vous devez d’abord vous assurer que vous avez initialisé le tableau afin qu’il soit suffisamment grand pour contenir le nouveau tableau. Vous pouvez le faire de deux façons :

- Utilisez le [ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md) instruction pour développer dynamiquement le tableau avant d’ajouter de nouveaux éléments à ce dernier. C’est la technique la plus simple, mais cela peut entraîner une dégradation des performances et la consommation excessive de la mémoire lorsque vous copiez des grands tableaux.
- Calculer le nombre total d’éléments requis pour le nouveau groupe de grande taille, puis ajoutez les éléments de chaque tableau source à ce dernier.

L’exemple suivant utilise la deuxième approche pour ajouter les quatre tableaux avec dix éléments à un seul tableau.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Étant donné que dans ce cas, les tableaux source sont tous les petits, nous pouvons développer également dynamiquement le tableau que nous ajoutons les éléments de chaque nouveau tableau à celui-ci. L’exemple suivant effectue cette opération.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Collections comme alternative aux tableaux

Les tableaux s’avèrent particulièrement utiles pour créer et utiliser un nombre fixe d’objets fortement typés. Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets. Contrairement aux tableaux, qui nécessitent que vous modifiez explicitement la taille d’un tableau avec la [ `ReDim` instruction](../../../language-reference/statements/redim-statement.md), collections augmenter et diminuer dynamiquement en fonction des besoins d’une application évoluent.

Lorsque vous utilisez `ReDim` pour redimensionner un tableau, Visual Basic crée un tableau et libère le précédent. Cela prend du temps d’exécution. Par conséquent, si le nombre d’éléments que vous utilisez change fréquemment, ou si vous ne pouvez pas prédire le nombre maximal d’éléments dont vous avez besoin, vous allez obtenir généralement de meilleures performances à l’aide d’une collection.

Pour certaines collections, vous pouvez affecter une clé à tout objet que vous placez dans la collection de sorte à pouvoir récupérer rapidement l’objet à l’aide de la clé.

Si votre collection contient des éléments d’un seul type de données, vous pouvez utiliser l’une des classes de l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> . Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté.

Pour plus d’informations sur les collections, consultez [Collections](../../concepts/collections.md).

## <a name="related-topics"></a>Rubriques connexes

|Terme|Définition|
|----------|----------------|
|[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)|Explique le rang et les dimensions des tableaux.|
|[Guide pratique pour Initialiser une Variable tableau en Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md)|Explique comment remplir les tableaux de valeurs initiales.|
|[Guide pratique pour Trier un tableau en Visual Basic](../../language-features/arrays/how-to-sort-an-array.md)|Montre comment trier les éléments d’un tableau par ordre alphabétique.|
|[Guide pratique pour Assigner un tableau à un autre tableau](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|Décrit les règles et les étapes à suivre pour assigner un tableau à une autre variable tableau.|
|[Dépannage des tableaux](../../language-features/arrays/troubleshooting-arrays.md)|Décrit des problèmes courants qui surviennent dans le cadre de l’utilisation de tableaux.|

## <a name="see-also"></a>Voir aussi

- <xref:System.Array?displayProperty=nameWithType>
- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
- [ReDim (instruction)](../../../language-reference/statements/redim-statement.md)
