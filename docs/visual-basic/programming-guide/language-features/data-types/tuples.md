---
title: Tuples
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 378ee4e7d3a3b106b719e5da819b09f336ff218e
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226658"
---
# <a name="tuples-visual-basic"></a>Tuples (Visual Basic)

À compter de Visual Basic 2017, le langage de Visual Basic offre une prise en charge intégrée des tuples qui facilitent la création de tuples et l’accès aux éléments de tuples. Un tuple est une structure de données légère qui possède un nombre et une séquence de valeurs spécifiques. Lorsque vous instanciez le tuple, vous définissez le nombre et le type de données de chaque valeur (ou élément). Par exemple, un 2 tuples (ou une paire) comporte deux éléments. La première peut être une `Boolean` valeur, tandis que la seconde est un `String` . Étant donné que les tuples facilitent le stockage de plusieurs valeurs dans un objet unique, ils sont souvent utilisés comme un moyen léger de retourner plusieurs valeurs à partir d’une méthode.

> [!IMPORTANT]
> La prise en charge des tuples requiert le <xref:System.ValueTuple> type. Si le .NET Framework 4,7 n’est pas installé, vous devez ajouter le package NuGet `System.ValueTuple` , qui est disponible dans la galerie NuGet. Sans ce package, vous pouvez obtenir une erreur de compilation semblable à la suivante : « le type prédéfini «ValueTuple (of,,,) » n’est pas défini ou importé».

## <a name="instantiating-and-using-a-tuple"></a>Instanciation et utilisation d’un tuple

Vous instanciez un tuple en plaçant ses valeurs délimitées par des virgules entre parenthèses. Chacune de ces valeurs devient alors un champ du tuple. Par exemple, le code suivant définit un triple (ou 3 tuples) avec `Date` comme première valeur, un `String` comme deuxième, et un `Boolean` comme troisième.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Par défaut, le nom de chaque champ dans un tuple se compose de la chaîne, `Item` avec la position de base un du champ dans le tuple. Pour ce tuple à 3 tuples, le champ est `Date` `Item1` , le `String` champ est `Item2` , et le `Boolean` champ est `Item3` . L’exemple suivant affiche les valeurs des champs du tuple instanciés dans la ligne de code précédente.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Les champs d’un tuple Visual Basic sont en lecture-écriture ; une fois que vous avez instancié un tuple, vous pouvez modifier ses valeurs. L’exemple suivant modifie deux des trois champs du tuple créé dans l’exemple précédent et affiche le résultat.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Instanciation et utilisation d’un tuple nommé

Au lieu d’utiliser des noms par défaut pour les champs d’un tuple, vous pouvez instancier un *Tuple nommé* en assignant vos propres noms aux éléments du tuple. Les champs du tuple sont ensuite accessibles par leurs noms attribués *ou* par leurs noms par défaut. L’exemple suivant instancie le même 3 tuples que précédemment, à ceci près qu’il nomme explicitement le premier champ `EventDate` , le deuxième `Name` et le troisième `IsHoliday` . Il affiche ensuite les valeurs de champ, les modifie, puis affiche à nouveau les valeurs de champ.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Noms des éléments de tuple inférés

À partir de Visual Basic 15,3, Visual Basic pouvez déduire les noms des éléments de Tuple ; vous n’avez pas à les assigner explicitement. Les noms de tuple déduits sont utiles lorsque vous initialisez un tuple à partir d’un ensemble de variables et que vous souhaitez que le nom d’élément de tuple soit identique au nom de la variable.

L’exemple suivant crée un `stateInfo` tuple qui contient trois éléments nommés explicitement, `state` , `stateName` et `capital` . Notez que, lorsque vous nommez les éléments, l’instruction d’initialisation de tuple affecte simplement les éléments nommés aux valeurs des variables portant le même nom.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

Étant donné que les éléments et les variables portent le même nom, le compilateur Visual Basic peut déduire les noms des champs, comme le montre l’exemple suivant.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Pour activer les noms d’éléments tuples déduits, vous devez définir la version du compilateur Visual Basic à utiliser dans votre fichier projet Visual Basic ( \* . vbproj) :

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

Le numéro de version peut être n’importe quelle version du compilateur Visual Basic à partir de 15,3. Au lieu de coder en dur une version spécifique du compilateur, vous pouvez également spécifier « latest » comme valeur de `LangVersion` pour compiler avec la version la plus récente du compilateur Visual Basic installé sur votre système.

Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../../../language-reference/configure-language-version.md).

Dans certains cas, le compilateur Visual Basic ne peut pas déduire le nom d’élément de tuple à partir du nom du candidat, et le champ de tuple ne peut être référencé qu’à l’aide de son nom par défaut, par exemple `Item1` ,, `Item2` etc. Il s’agit notamment des éléments suivants :

- Le nom du candidat est le même que le nom d’un membre de tuple, tel que `Item3` , `Rest` ou `ToString` .

- Le nom du candidat est dupliqué dans le tuple.

Lorsque l’inférence de nom de champ échoue, Visual Basic ne génère pas d’erreur de compilateur et n’est pas une exception levée au moment de l’exécution. Au lieu de cela, les champs de tuple doivent être référencés par leurs noms prédéfinis, tels que `Item1` et `Item2` .

## <a name="tuples-versus-structures"></a>Tuples et structures

Un tuple Visual Basic est un type valeur qui est une instance de l’un des types génériques **System. ValueTuple** . Par exemple, le `holiday` Tuple défini dans l’exemple précédent est une instance de la <xref:System.ValueTuple%603> structure. Il est conçu pour être un conteneur léger de données. Étant donné que le tuple a pour but de faciliter la création d’un objet avec plusieurs éléments de données, il manque certaines des fonctionnalités qu’une structure personnalisée peut avoir. notamment :

- Membres personnalisés. Vous ne pouvez pas définir vos propres propriétés, méthodes ou événements pour un tuple.

- Métrage. Vous ne pouvez pas valider les données assignées à des champs.

- Altér. Les tuples Visual Basic sont mutables. En revanche, une structure personnalisée vous permet de contrôler si une instance est mutable ou immuable.

Si les membres personnalisés, la validation de propriété et de champ ou l’immuabilité sont importants, vous devez utiliser l’instruction Visual Basic [structure](../../../language-reference/statements/structure-statement.md) pour définir un type de valeur personnalisé.

Un tuple Visual Basic hérite des membres de son type **ValueTuple** . En plus de ses champs, il s’agit des méthodes suivantes :

| Membre | Description |
| ---|---|
| CompareTo | Compare le tuple actuel à un autre Tuple avec le même nombre d’éléments. |
| Est égal à | Détermine si le tuple actuel est égal à un autre tuple ou objet. |
| GetHashCode | Calcule le code de hachage pour l’instance actuelle. |
| ToString | Retourne la représentation sous forme de chaîne de ce tuple, qui prend la forme `(Item1, Item2...)` , où `Item1` et `Item2` représentent les valeurs des champs du tuple. |

En outre, les types **ValueTuple** implémentent les <xref:System.Collections.IStructuralComparable> <xref:System.Collections.IStructuralEquatable> interfaces et, qui vous permettent de définir des comparateurs de clients.

## <a name="assignment-and-tuples"></a>Affectation et tuples

Visual Basic prend en charge l’assignation entre les types tuple qui ont le même nombre de champs. Les types de champs peuvent être convertis si l’une des conditions suivantes est vraie :

- Les champs source et cible sont du même type.

- Une conversion étendue (ou implicite) du type de source vers le type cible est définie.

- `Option Strict`est `On` , et une conversion restrictive (ou explicite) du type source vers le type cible est définie. Cette conversion peut lever une exception si la valeur source est en dehors de la plage du type cible.

Les autres conversions ne sont pas prises en compte pour les affectations. Examinons les types d’affectation qui sont autorisés entre les types tuple.

Prenez en compte les variables utilisées dans les exemples suivants :

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

Les deux premières variables, `unnamed` et `anonymous` , n’ont pas de noms sémantiques fournis pour les champs. Leurs noms de champs sont les valeurs par défaut `Item1` et `Item2` . Les deux dernières variables, `named` et `differentName` ont des noms de champ sémantique. Notez que ces deux tuples ont des noms différents pour les champs.

Ces quatre tuples ont le même nombre de champs (appelé « arité ») et les types de ces champs sont identiques. Par conséquent, toutes ces affectations fonctionnent :

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notez que les noms des tuples ne sont pas affectés. Les valeurs des champs sont affectées suivant l’ordre des champs dans le tuple.

Enfin, Notez que nous pouvons assigner le `named` Tuple au `conversion` tuple, même si le premier champ de `named` est un `Integer` et que le premier champ de `conversion` est un `Long` . Cette assignation est réussie, car la conversion d’un `Integer` en `Long` est une conversion étendue.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Les tuples avec différents nombres de champs ne peuvent pas être assignés :

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuples comme valeurs de retour de méthode

Une méthode ne peut retourner qu’une seule valeur. Bien souvent, vous aimeriez qu’un appel de méthode retourne plusieurs valeurs. Il existe plusieurs façons de contourner cette limitation :

- Vous pouvez créer une classe ou une structure personnalisée dont les propriétés ou les champs représentent des valeurs retournées par la méthode. C’est donc une solution à haute densité ; pour cela, vous devez définir un type personnalisé dont le seul but est de récupérer des valeurs à partir d’un appel de méthode.

- Vous pouvez retourner une valeur unique à partir de la méthode et retourner les valeurs restantes en les passant par référence à la méthode. Cela implique la surcharge liée à l’instanciation d’une variable et les risques de remplacement par inadvertance de la valeur de la variable que vous transmettez par référence.

- Vous pouvez utiliser un tuple, qui fournit une solution légère pour récupérer plusieurs valeurs de retour.

Par exemple, les méthodes **TryParse** dans .net retournent une `Boolean` valeur qui indique si l’opération d’analyse a réussi. Le résultat de l’opération d’analyse est retourné dans une variable passée par référence à la méthode. Normalement, un appel à la méthode d’analyse, comme <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> celui-ci, se présente comme suit :

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Nous pouvons retourner un tuple à partir de l’opération d’analyse si nous encapsulerons l’appel à la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode dans notre propre méthode. Dans l’exemple suivant, `NumericLibrary.ParseInteger` appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode et retourne un tuple nommé avec deux éléments.

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Vous pouvez ensuite appeler la méthode avec un code semblable au suivant :

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic des tuples et des tuples dans le .NET Framework

Un tuple Visual Basic est une instance de l’un des types génériques **System. ValueTuple** , qui ont été introduits dans le .NET Framework 4,7. Le .NET Framework comprend également un ensemble de classes **System. Tuple** génériques. Toutefois, ces classes diffèrent de Visual Basic tuples et des types génériques **System. ValueTuple** de plusieurs façons :

- Les éléments des classes **Tuple** sont des propriétés nommées `Item1` , `Item2` , et ainsi de suite. Dans Visual Basic tuples et les types **ValueTuple** , les éléments Tuple sont des champs.

- Vous ne pouvez pas assigner des noms explicites aux éléments d’une instance de **Tuple** ou d’une instance de **ValueTuple** . Visual Basic vous permet d’attribuer des noms qui communiquent la signification des champs.

- Les propriétés d’une instance de **Tuple** sont en lecture seule ; les tuples sont immuables. Dans Visual Basic les tuples et les types **ValueTuple** , les champs de tuple sont en lecture-écriture ; les tuples sont mutables.

- Les types de **tuples** génériques sont des types référence. L’utilisation de ces types de **tuples** signifie l’allocation d’objets. Sur des chemins réactifs, cela peut avoir un impact mesurable sur les performances de votre application. Visual Basic tuples et les types **ValueTuple** sont des types valeur.

Les méthodes d’extension dans la <xref:System.TupleExtensions> classe facilitent la conversion entre les tuples Visual Basic et les objets de **Tuple** .net. La méthode **ToTuple** convertit un tuple Visual Basic en objet de **Tuple** .net, et la méthode **ToValueTuple** convertit un objet de **Tuple** .net en un tuple Visual Basic.

L’exemple suivant crée un tuple, le convertit en objet de **Tuple** .net et le convertit en un tuple Visual Basic. L’exemple compare ensuite ce tuple avec celui d’origine pour s’assurer qu’ils sont égaux.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](index.md)
