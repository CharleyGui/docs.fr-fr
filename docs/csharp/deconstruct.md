---
title: Déconstruction de tuples et d’autres types
description: Découvrez comment déconstruire des tuples et d’autres types.
ms.technology: csharp-fundamentals
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 23d193faf9702628698fe558f6667aeb130e8916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100668"
---
# <a name="deconstructing-tuples-and-other-types"></a>Déconstruction de tuples et d’autres types

Un tuple offre un moyen léger de récupérer plusieurs valeurs à partir d’un appel de méthode. Cependant, une fois que vous récupérez le tuple, vous devez gérer ses éléments individuels. Cette gestion élément par élément est assez fastidieuse, comme le montre l’exemple suivant. La méthode `QueryCityData` retourne un tuple de 3 éléments, et chacun de ses éléments est affecté à une variable dans une opération distincte.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

La récupération de plusieurs valeurs de champs et de propriétés d’un objet peut également être assez fastidieuse : vous devez affecter une valeur de champ ou de propriété à une variable membre par membre.

À compter de C# 7.0, vous pouvez récupérer plusieurs éléments d’un tuple ou récupérer plusieurs valeurs de champ et de propriété, ainsi que des valeurs calculées, à partir d’un objet en une seule opération de *déconstruction*. Quand vous déconstruisez un tuple, vous affectez ses éléments à des variables individuelles. Quand vous déconstruisez un objet, vous affectez des valeurs sélectionnées à des variables individuelles.

## <a name="deconstructing-a-tuple"></a>Déconstruction d’un tuple

Des fonctionnalités C# intégrées prennent en charge la déconstruction des tuples, ce qui vous permet de décomposer tous les éléments d’un tuple en une seule opération. La syntaxe générale de déconstruction d’un tuple est similaire à la syntaxe qui permet d’en définir un : vous placez les variables auxquelles chaque élément doit être affecté entre des parenthèses, dans la partie gauche d’une instruction d’affectation. Par exemple, l’instruction suivante affecte les éléments d’un tuple de 4 éléments à quatre variables distinctes :

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Il existe trois façons de déconstruire un tuple :

- Vous pouvez déclarer explicitement le type de chaque champ entre des parenthèses. L’exemple suivant utilise cette approche pour déconstruire un tuple de 3 éléments retourné par la méthode `QueryCityData`.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Vous pouvez utiliser le mot clé `var` pour que C# infère le type de chaque variable. Vous placez le mot clé `var` en dehors des parenthèses. L’exemple suivant utilise l’inférence de type lors de la déconstruction du tuple de 3 éléments retourné par la méthode `QueryCityData`.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Vous pouvez aussi utiliser le mot clé `var` individuellement avec tout ou partie des déclarations de variables à l’intérieur des parenthèses.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Ceci est assez fastidieux et n’est pas recommandé.

- Enfin, vous pouvez déconstruire le tuple dans des variables qui ont déjà été déclarées.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Notez que vous ne pouvez pas spécifier un type spécifique en dehors des parenthèses, même si tous les champs du tuple ont le même type. Cela génère l’erreur du compilateur CS8136, « La déconstruction de 'var (...)' form interdit un type spécifique pour 'var'.».

Notez que vous devez également affecter chaque élément du tuple à une variable. Si vous omettez des éléments, le compilateur génère l’erreur CS8132, « Impossible de déconstruire un tuple de « x » éléments en « y » variables ».

Notez que vous ne pouvez pas mélanger des déclarations et des affectations à des variables existantes sur le côté gauche d’une déconstruction. Le compilateur génère l’erreur CS8184, « Une déconstruction ne peut pas contenir à la fois des déclarations et des expressions à gauche », quand les membres incluent des variables nouvellement déclarées et des variables existantes.

## <a name="deconstructing-tuple-elements-with-discards"></a>Déconstruction d’éléments d’un tuple en ignorant des éléments

Souvent, lors de la déconstruction d’un tuple, vous êtes intéressé seulement par les valeurs de certains éléments. À compter de C# 7.0, vous pouvez tirer parti de la prise en charge des *éléments ignorés*, qui sont des variables en écriture seule dont vous avez choisi d’ignorer les valeurs. Un élément ignoré est désigné par un caractère de soulignement (« \_ ») dans une affectation. Vous pouvez ignorer autant de valeurs que vous le souhaitez ; pour représenter toutes les valeurs, utilisez l’élément ignoré unique, `_`.

L’exemple suivant illustre l’utilisation de tuples avec des éléments ignorés. La méthode `QueryCityDataForYears` retourne un tuple de 6 éléments avec le nom d’une ville, sa région, une année, la population de la ville pour cette année, une seconde année et la population de la ville pour cette seconde année. L’exemple montre la différence de population entre ces deux années. Parmi les données disponibles dans le tuple, nous ne sommes pas intéressés par la région de la ville, et nous connaissons le nom de la ville et les deux dates au moment du design. Par conséquent, nous sommes intéressés seulement par les deux valeurs de la population stockées dans le tuple et nous pouvons gérer ses valeurs restantes comme éléments ignorés.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Déconstruction de types définis par l’utilisateur

C# n’offre pas de prise en charge intégrée pour déconstruire les types non-tuple. Cependant, en tant que créateur d’une classe, d’un struct ou d’une interface, vous pouvez permettre la déconstruction du type en implémentant une ou plusieurs méthodes `Deconstruct`. La méthode retourne void, et chaque valeur à déconstruire est indiquée par un paramètre [out](language-reference/keywords/out-parameter-modifier.md) dans la signature de la méthode. Par exemple, la méthode `Deconstruct` suivante d’une classe `Person` retourne le prénom, le deuxième prénom et le nom :

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Vous pouvez alors déconstruire une instance de la classe `Person` nommée `p` avec une affectation comme celle-ci :

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

L’exemple suivant surcharge la méthode `Deconstruct` de façon retourner différentes combinaisons des propriétés d’un objet `Person`. Les différentes surcharges retournent :

- Un prénom et un nom.
- Un prénom, un nom et un deuxième nom.
- Un prénom, un nom, un nom de ville et un nom d’état.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Comme vous pouvez surcharger la méthode `Deconstruct` de façon à refléter les groupes de données qui sont souvent extraits d’un objet, vous devez être attentif à définir des méthodes `Deconstruct` avec des signatures qui les distinguent et ne sont pas ambiguës. Plusieurs méthodes `Deconstruct` ayant même nombre de paramètres `out`, ou le même nombre et le même type de paramètres `out` dans un ordre différent, peuvent provoquer de la confusion.

La méthode `Deconstruct` surchargée dans l’exemple suivant montre une source possible de confusion. La première surcharge retourne le prénom, le deuxième prénom, le nom et l’âge d’un objet `Person`, dans cet ordre. La seconde surcharge retourne les informations de nom seulement avec le revenu annuel, mais le prénom, le deuxième prénom et le nom sont dans un ordre différent. Ceci facilite la confusion dans l’ordre des arguments lors de la déconstruction d’une instance de `Person`.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Déconstruction d’un type défini par l’utilisateur avec des éléments ignorés

Tout comme vous le faites avec des [tuples](#deconstructing-tuple-elements-with-discards), vous pouvez utiliser des éléments ignorés pour ignorer des éléments sélectionnés retournés par une méthode `Deconstruct`. Chaque élément ignoré est défini par une variable nommée « \_ », et une même opération de déconstruction peut inclure plusieurs éléments ignorés.

L’exemple suivant déconstruit un objet `Person` en quatre chaînes (le prénom et le nom, la ville et l’état), mais ignore le nom et l’état.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Déconstruction d’un type défini par l’utilisateur avec une méthode d’extension

Si vous n’avez pas créé une classe, un struct ou une interface, vous pouvez néanmoins déconstruire des objets de ce type en implémentant une ou plusieurs `Deconstruct` [méthodes d’extension](programming-guide/classes-and-structs/extension-methods.md) pour retourner les valeurs qui vous intéressent.

L’exemple suivant définit deux méthodes d’extension `Deconstruct` pour la classe <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType>. La première retourne un ensemble de valeurs qui indique les caractéristiques de la propriété, notamment son type, si elle est statique ou d’instance, si elle est en lecture seule et si elle est indexée. La seconde indique l’accessibilité de la propriété. Comme l’accessibilité des accesseurs get et set peut varier, des valeurs booléennes indiquent si la propriété a des accesseurs get et set distincts et, le cas échéant, s’ils ont la même accessibilité. S’il n’existe qu’un seul accesseur, ou si les deux accesseurs get et set ont la même accessibilité, la variable `access` indique l’accessibilité de la propriété comme un tout. Sinon, l’accessibilité des accesseurs get et set est indiquée par les variables `getAccess` et `setAccess`.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Voir aussi

- [Éléments ignorés](discards.md)
- [Tuples](tuples.md)
