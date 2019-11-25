---
title: Tableaux
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 9dfe7814b00b4d060fa4ab9aa594faa948217d8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351866"
---
# <a name="arrays-in-visual-basic"></a>Tableaux dans Visual Basic

An array is a set of values, which are termed *elements*, that are logically related to each other. For example, an array may consist of the number of students in each grade in a grammar school; each element of the array is the number of students in a single grade. Similarly, an array may consist of a student's grades for a class; each element of the array is a single grade.

It is possible individual variables to store each of our data items. For example, if our application analyzes student grades, we can use a separate variable for each student's grade, such as `englishGrade1`, `englishGrade2`, etc. This approach has three major limitations:

- We have to know at design time exactly how many grades we have to handle.
- Handling large numbers of grades quickly becomes unwieldy. This in turn makes an application much more likely to have serious bugs.
- It is difficult to maintain. Each new grade that we add requires that the application be modified, recompiled, and redeployed.

By using an array, you can refer to these related values by the same name, and use a number that’s called an *index* or *subscript* to identify an individual element based on its position in the array. The indexes of an array range from 0 to one less than the total number of elements in the array. When you use Visual Basic syntax to define the size of an array, you specify its highest index, not the total number of elements in the array. You can work with the array as a unit, and the ability to iterate its elements frees you from needing to know exactly how many elements it contains at design time.

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

## <a name="array-elements-in-a-simple-array"></a>Array elements in a simple array

Let's create an array named `students` to store the number of students in each grade in a grammar school. Les index des éléments s’échelonnent de 0 à 6. Using this array is simpler than declaring seven variables.

The following illustration shows the `students` array. Pour chaque élément du tableau :

- L’index de l’élément représente le niveau scolaire (l’index 0 représente le niveau maternelle).

- La valeur contenue dans l’élément représente le nombre d’élèves de cette catégorie.

![Diagram showing an array of the numbers of students](./media/index/students-array-elements.gif)

The following example contains the Visual Basic code that creates and uses the array:

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

The example does three things:

- It declares a `students` array with seven elements. The number `6` in the array declaration indicates the last index in the array; it is one less than the number of elements in the array.
- It assigns values to each element in the array. Array elements are accessed by using the array name and including the index of the individual element in parentheses.
- It lists each value of the array. The example uses a [`For`](../../../language-reference/statements/for-next-statement.md) statement to access each element of the array by its index number.

The `students` array in the preceding example is a one-dimensional array because it uses one index. An array that uses more than one index or subscript is called *multidimensional*. For more information, see the rest of this article and [Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md).

## <a name="creating-an-array"></a>Creating an array

You can define the size of an array in several ways:

- You can specify the size when the array is declared:

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- You can use a `New` clause to supply the size of an array when it’s created:

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

If you have an existing array, you can redefine its size by using the [`ReDim`](../../../language-reference/statements/redim-statement.md) statement. You can specify that the `ReDim` statement keep the values that are in the array, or you can specify that it create an empty array. L’exemple suivant montre les différentes utilisations possibles de l’instruction `ReDim` pour modifier la taille d’un tableau existant.

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

For more information, see the [ReDim Statement](../../../language-reference/statements/redim-statement.md).

## <a name="storing-values-in-an-array"></a>Storing values in an array

Vous pouvez accéder à chaque emplacement d’un tableau en utilisant un index de type `Integer`. Vous pouvez stocker des valeurs dans un tableau et les récupérer par la suite en référençant chaque emplacement du tableau en utilisant son index entre parenthèses. Indexes for multidimensional arrays are separated by commas (,). Vous avez besoin d’un index pour chaque dimension de tableau.

The following example shows some statements that store and retrieve values in arrays.

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>Populating an array with array literals

By using an array literal, you can populate an array with an initial set of values at the same time that you create it. Un littéral de tableau se compose d’une liste de valeurs séparées par des virgules mise entre accolades (`{}`).

Quand vous créez un tableau en utilisant un littéral de tableau, vous pouvez soit indiquer le type du tableau, soit utiliser l’inférence de type pour déterminer le type du tableau. The following example shows both options.

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

When you use type inference, the type of the array is determined by the *dominant type* in the list of literal values. The dominant type is the type to which all other types in the array can widen. Si ce type unique ne peut pas être déterminé, le type dominant est le type unique auquel tous les autres types du tableau peuvent se réduire. Si aucun de ces types uniques ne peut être déterminé, le type dominant est `Object`. Par exemple, si la liste de valeurs fournie au littéral de tableau contient des valeurs de type `Integer`, `Long`et `Double`, le tableau qui en résulte est de type `Double`. Because `Integer` and `Long` widen only to `Double`, `Double` is the dominant type. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md).

> [!NOTE]
> You can use type inference only for arrays that are defined as local variables in a type member. If an explicit type definition is absent, arrays defined with array literals at the class level are of type `Object[]`. For more information, see [Local type inference](../variables/local-type-inference.md).

Note that the previous example defines `values` as an array of type `Double` even though all the array literals are of type `Integer`. You can create this array because the values in the array literal can widen to `Double` values.

You can also create and populate a multidimensional array by using *nested array literals*. Nested array literals must have a number of dimensions that’s consistent with the resulting array. The following example creates a two-dimensional array of integers by using nested array literals.

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

When using nested array literals to create and populate an array, an error occurs if the number of elements in the nested array literals don't match. An error also occurs if you explicitly declare the array variable to have a different number of dimensions than the array literals.

Just as you can for one-dimensional arrays, you can rely on type inference when creating a multidimensional array with nested array literals. The inferred type is the dominant type for all the values in all the array literals for all nesting level. The following example creates a two-dimensional array of type `Double[,]` from values that are of type `Integer` and `Double`.

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

Pour obtenir des exemples supplémentaires, consultez [Comment : initialiser une variable tableau en Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).

## <a name="iterating-through-an-array"></a>Iterating through an array

When you iterate through an array, you access each element in the array from the lowest index to the highest or from the highest to the lowest. Typically, use either the [For...Next Statement](../../../language-reference/statements/for-next-statement.md) or the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) to iterate through the elements of an array. When you don't know the upper bounds of the array, you can call the <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> method to get the highest value of the index. Although lowest index value is almost always 0, you can call the <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> method to get the lowest value of the index.

The following example iterates through a one-dimensional array by using the [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

The following example iterates through a multidimensional array by using a [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement. La méthode <xref:System.Array.GetUpperBound%2A> dispose d’un paramètre qui spécifie la dimension. `GetUpperBound(0)` returns the highest index of the first dimension, and `GetUpperBound(1)` returns the highest index of the second dimension.

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

The following example uses a [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md)to iterate through a one-dimensional array and a two-dimensional array.

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>Array size

La taille d’un tableau est le produit des longueurs de toutes ses dimensions. Elle représente le nombre total d’éléments actuellement contenus dans le tableau.  For example, the following example declares a 2-dimensional array with four elements in each dimension. As the output from the example shows, the array's size is 16 (or (3 + 1) * (3 + 1).

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> This discussion of array size does not apply to jagged arrays. For information on jagged arrays and determining the size of a jagged array, see the [Jagged arrays](#jagged-arrays) section.

Vous pouvez trouver la taille d’un tableau en utilisant la propriété <xref:System.Array.Length%2A?displayProperty=nameWithType>. You can find the length of each dimension of a multidimensional array by using the <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.

You can resize an array variable by assigning a new array object to it or by using the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md) statement. The following example uses the `ReDim` statement to change a 100-element array to a 51-element array.

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

Il y a plusieurs points à prendre en compte en ce qui concerne la taille d’un tableau.

|||
|---|---|
|Longueur de dimension|The index of each dimension is 0-based, which means it ranges from 0 to its upper bound. Therefore, the length of a given dimension is one greater than the declared upper bound of that dimension.|
|Limites de longueur|The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is <xref:System.Int32.MaxValue?displayProperty=nameWithType> or (2 ^ 31) - 1. Cependant, la taille totale d’un tableau est aussi limitée par la mémoire disponible sur votre système. If you attempt to initialize an array that exceeds the amount of available memory, the runtime throws an <xref:System.OutOfMemoryException>.|
|Taille et taille d’élément|La taille d’un tableau est indépendante du type de données de ses éléments. The size always represents the total number of elements, not the number of bytes that they consume in memory.|
|Consommation de mémoire|Il est déconseillé de faire des hypothèses sur la façon dont un tableau est stocké en mémoire. Le stockage varie selon la largeur de données de la plateforme. Par exemple, un même tableau utilise plus de mémoire sur un système 64 bits que sur un système 32 bits. Selon la configuration du système au moment de l’initialisation d’un tableau, le Common Language Runtime (CLR) peut assigner du stockage de façon à regrouper les éléments aussi près que possible les uns des autres ou pour tous les adapter aux limites matérielles naturelles. De même, un tableau nécessite un supplément de stockage pour ses informations de contrôle, un supplément qui augmente d’autant à chaque dimension ajoutée.|

## <a name="the-array-type"></a>The array type

Every array has a data type, which differs from the data type of its elements. Le type de données varie d’un tableau à un autre. En effet, le type de données d’un tableau est déterminé par le nombre de dimensions (ou *rang*) qu’il possède et par le type de données de ses éléments. Two array variables are of the same data type only when they have the same rank and their elements have the same data type. The lengths of the dimensions of an array do not influence the array data type.

Chaque tableau hérite de la classe <xref:System.Array?displayProperty=nameWithType> et vous pouvez déclarer une variable de type `Array`, mais vous ne pouvez pas créer un tableau de type `Array`. For example, although the following code declares the `arr` variable to be of type `Array` and calls the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method to instantiate the array, the array's type proves to be Object[].

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

De même, [l’instruction ReDim](../../../language-reference/statements/redim-statement.md) ne peut pas opérer sur une variable déclarée comme étant du type `Array`. For these reasons, and for type safety, it is advisable to declare every array as a specific type.

Vous pouvez déterminer le type de données d’un tableau ou de ses éléments de plusieurs façons.

- You can call the <xref:System.Object.GetType%2A> method on the variable to get a <xref:System.Type> object that represents the run-time type of the variable. L’objet <xref:System.Type> contient des informations complètes dans ses propriétés et méthodes.
- You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to get a `String` with the name of run-time type.

The following example calls the both the `GetType` method and the `TypeName` function to determine the type of an array. The array type is `Byte(,)`. Note that the <xref:System.Type.BaseType%2A?displayProperty=nameWithType> property also indicates that the base type of the byte array is the <xref:System.Array> class.

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>Arrays as return values and parameters

Pour retourner un tableau à partir d’une procédure `Function`, spécifiez le type de données du tableau et le nombre de dimensions en tant que type de retour de [l’instruction Function](../../../language-reference/statements/function-statement.md). Dans la fonction, déclarez une variable tableau locale avec le même type de données et le même nombre de dimensions. Dans [l’instruction Return](../../../language-reference/statements/return-statement.md), incluez la variable tableau locale sans parenthèses.

Pour spécifier un tableau en tant que paramètre d’une procédure `Sub` ou `Function` , définissez le paramètre en tant que tableau avec un type de données et un nombre de dimensions spécifiés. In the call to the procedure, pass an array variable with the same data type and number of dimensions.

In the following example, the `GetNumbers` function returns an `Integer()`, a one-dimensional array of type `Integer`. La procédure `ShowNumbers` accepte un argument `Integer()` .

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`, a two-dimensional array of type `Integer`.  La procédure `ShowNumbersMultiDim` accepte un argument `Integer(,)` .

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>Tableaux en escalier

Parfois, la structure de données de votre application est à deux dimensions, mais pas rectangulaire. For example, you might use an array to store data about the high temperature of each day of the month. The first dimension of the array represents the month, but the second dimension represents the number of days, and the number of days in a month is not uniform. A *jagged array*, which is also called an *array of arrays*, is designed for such scenarios. A jagged array is an array whose elements are also arrays. Un tableau en escalier et chaque élément qu’il contient peut avoir une ou plusieurs dimensions.

The following example uses an array of months, each element of which is an array of days. The example uses a jagged array because different months have different numbers of days.  The example shows how to create a jagged array, assign values to it, and retrieve and display its values.

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

The previous example assigns values to the jagged array on an element-by-element basis by using a `For...Next` loop. You can also assign values to the elements of a jagged array by using nested array literals. However, the attempt to use nested array literals (for example, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) generates compiler error [BC30568](../../../,,/../misc/bc30568.md). To correct the error, enclose the inner array literals in parentheses. The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following example shows.

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

A jagged array is a one-dimensional array whose elements contain arrays. Therefore, the <xref:System.Array.Length%2A?displayProperty=nameWithType> property and the `Array.GetLength(0)` method return the number of elements in the one-dimensional array, and `Array.GetLength(1)` throws an <xref:System.IndexOutOfRangeException> because a jagged array is not multidimensional. You determine the number of elements in each subarray by retrieving the value of each subarray's <xref:System.Array.Length%2A?displayProperty=nameWithType> property. The following example illustrates how to determine the number of elements in a jagged array.

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>Zero-length arrays

Visual Basic differentiates between a uninitialized array (an array whose value is `Nothing`) and a *zero-length array* or empty array (an array that has no elements.) An uninitialized array is one that has not been dimensioned or had any values assigned to it. Exemple :

```vb
Dim arr() As String
```

A zero-length array is declared with a dimension of -1. Exemple :

```vb
Dim arrZ(-1) As String
```

Vous pouvez être amené à créer un tableau de longueur zéro dans les cas suivants :

- Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a Visual Basic function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.

- You want to keep your code simple by not having to check for `Nothing` as a special case.

- Votre code interagit avec une interface de programmation d’applications (API) qui vous oblige à passer un tableau de longueur zéro à une ou plusieurs procédures ou qui retourne un tableau de longueur zéro à partir d’une ou plusieurs procédures.

## <a name="splitting-an-array"></a>Splitting an array

In some cases, you may need to split a single array into multiple arrays. This involves identifying the point or points at which the array is to be split, and then spitting the array into two or more separate arrays.

> [!NOTE]
> This section does not discuss splitting a single string into a string array based on some delimiter. For information on splitting a string, see the <xref:System.String.Split%2A?displayProperty=nameWithType> method.

The most common criteria for splitting an array are:

- Nombre d’éléments dans le tableau. For example, you might want to split an array of more than a specified number of elements into a number of approximately equal parts. For this purpose, you can use the value returned by either the <xref:System.Array.Length%2A?displayProperty=nameWithType> or <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.

- The value of an element, which serves as a delimiter that indicates where the array should be split. You can search for a specific value by calling the <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> and <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> methods.

Once you've determined the index or indexes at which the array should be split, you can then create the individual arrays by calling the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.

The following example splits an array into two arrays of approximately equal size. (If the total number of array elements is odd, the first array has one more element than the second.)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

The following example splits a string array into two arrays based on the presence of an element whose value is "zzz", which serves as the array delimiter. The new arrays do not include the element that contains the delimiter.

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>Joining arrays

You can also combine a number of arrays into a single larger array. To do this, you also use the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.

> [!NOTE]
> This section does not discuss joining a string array into a single string. For information on joining a string array, see the <xref:System.String.Join%2A?displayProperty=nameWithType> method.

Before copying the elements of each array into the new array, you must first ensure that you have initialized the array so that it is large enough to accommodate the new array. Vous pouvez le faire de deux façons :

- Use the [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) statement to dynamically expand the array before adding new elements to it. This is the easiest technique, but it can result in performance degradation and excessive memory consumption when you are copying large arrays.
- Calculate the total number of elements needed for the new large array, then add the elements of each source array to it.

The following example uses the second approach to add four arrays with ten elements each to a single array.

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

Since in this case the source arrays are all small, we can also dynamically expand the array as we add the elements of each new array to it. L’exemple suivant effectue cette opération.

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>Collections as an alternative to arrays

Les tableaux s’avèrent particulièrement utiles pour créer et utiliser un nombre fixe d’objets fortement typés. Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets. Unlike arrays, which require that you explicitly change the size of an array with the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md), collections grow and shrink dynamically as the needs of an application change.

When you use `ReDim` to redimension an array, Visual Basic creates a new array and releases the previous one. Cela prend du temps d’exécution. Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you'll usually obtain better performance by using a collection.

Pour certaines collections, vous pouvez affecter une clé à tout objet que vous placez dans la collection de sorte à pouvoir récupérer rapidement l’objet à l’aide de la clé.

Si votre collection contient des éléments d’un seul type de données, vous pouvez utiliser une des classes dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType>. Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté.

Pour plus d’informations sur les collections, consultez [Collections](../../concepts/collections.md).

## <a name="related-topics"></a>Rubriques connexes

|Terme|Définition|
|----------|----------------|
|[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)|Explique le rang et les dimensions des tableaux.|
|[Comment : initialiser une variable tableau en Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md)|Explique comment remplir les tableaux de valeurs initiales.|
|[Comment : trier un tableau dans Visual Basic](../../language-features/arrays/how-to-sort-an-array.md)|Montre comment trier les éléments d’un tableau par ordre alphabétique.|
|[Guide pratique : assigner un tableau à un autre tableau](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|Décrit les règles et les étapes à suivre pour assigner un tableau à une autre variable tableau.|
|[Dépannage des tableaux](../../language-features/arrays/troubleshooting-arrays.md)|Décrit des problèmes courants qui surviennent dans le cadre de l’utilisation de tableaux.|

## <a name="see-also"></a>Voir aussi

- <xref:System.Array?displayProperty=nameWithType>
- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
- [ReDim (instruction)](../../../language-reference/statements/redim-statement.md)
