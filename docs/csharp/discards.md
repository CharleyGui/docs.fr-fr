---
title: Éléments ignorés - Guide C#
description: Décrit la prise en charge par C# des éléments ignorés, qui sont des variables qui peuvent être ignorées, et les différentes façons dont les éléments ignorés peuvent être utilisés.
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: a76e7fc13f92ec0de87153bb35eb3924bb317616
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100640"
---
# <a name="discards---c-guide"></a>Éléments ignorés - Guide C#

À compter de C# 7.0, les éléments ignorés sont pris en charge. Il s’agit de variables temporaires factices, qui sont inutilisées de façon intentionnelle dans le code d’une application. Les éléments ignorés sont équivalents à des variables non affectées : elles n’ont pas de valeur. Comme il n’existe qu’une seule variable d’élément ignoré et qu’un stockage ne peut même pas lui être alloué, les éléments ignorés peuvent réduire les allocations de mémoire. Dans la mesure où elles éclairent l’intention de votre code, elles améliorent sa lisibilité et sa maintenabilité.

Vous indiquez qu’une variable est un élément ignoré en lui affectant comme nom le trait de soulignement (`_`). Par exemple, l’appel de méthode suivant retourne un tuple de 3 éléments dans lequel les première et deuxième valeurs sont ignorées et dans lequel *area* est une variable précédemment déclarée à laquelle vous devez affecter le troisième composant correspondant retourné par *GetCityInformation* :

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

Dans C# 7.0, les éléments ignorés sont pris en charge dans les affectations dans les contextes suivants :

- Tuple et [la déconstruction d’objets](deconstruct.md).
- Critères spéciaux avec [is](language-reference/keywords/is.md) et [switch](language-reference/keywords/switch.md).
- Appels à des méthodes avec des paramètres `out`.
- Un `_` autonome quand aucun `_` n’est dans l’étendue.

Quand `_` est un élément ignoré valide, une tentative de récupérer sa valeur ou de l’utiliser dans une opération d’affectation génère l’erreur de compilateur CS0301, « Le nom '\_' n’existe pas dans le contexte actuel ». La raison en est qu’aucune valeur n’est affectée à `_` et qu’il n’est même pas possible de lui affecter un emplacement de stockage. S’il s’agissait d’une variable réelle, vous ne pourriez pas ignorer plus d’une valeur, comme l’a fait l’exemple précédent.

## <a name="tuple-and-object-deconstruction"></a>Déconstruction de tuple et d’objet

Les éléments ignorés sont particulièrement utiles pour travailler avec des tuples quand le code de votre application utilise certains éléments d’un tuple mais ignore les autres. Par exemple, la méthode `QueryCityDataForYears` suivante retourne un tuple de 6 éléments avec le nom d’une ville, sa région, une année, la population de la ville pour cette année, une seconde année et la population de la ville pour cette seconde année. L’exemple montre la différence de population entre ces deux années. Parmi les données disponibles dans le tuple, nous ne sommes pas intéressés par la région de la ville, et nous connaissons le nom de la ville et les deux dates au moment du design. Par conséquent, nous sommes intéressés seulement par les deux valeurs de la population stockées dans le tuple et nous pouvons gérer ses valeurs restantes comme éléments ignorés.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Pour plus d’informations sur la déconstruction de tuples avec des éléments ignorés, consultez [Déconstruction de tuples et d’autres types](deconstruct.md#deconstructing-tuple-elements-with-discards).

La méthode `Deconstruct` d’une classe, d’un struct ou d’une interface vous permet aussi de récupérer et de déconstruire un ensemble spécifique de données d’un objet. Vous pouvez utiliser des éléments ignorés quand vous êtes intéressé seulement par un sous-ensemble des valeurs déconstruites. L’exemple suivant déconstruit un objet `Person` en quatre chaînes (le prénom, le nom, la ville et l’État), mais ignore le nom et l’État.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Pour plus d’informations sur la déconstruction de types définis par l’utilisateur avec des éléments ignorés, consultez [Déconstruction de tuples et d’autres types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Critères spéciaux avec `switch` et `is`

Le *modèle d’élément ignoré* peut être utilisé dans des critères spéciaux avec les mots clés [is](language-reference/keywords/is.md) et [switch](language-reference/keywords/switch.md). Chaque expression correspond toujours au modèle d’élément ignoré.

L’exemple suivant définit une méthode `ProvidesFormatInfo` qui utilise des instructions [is](language-reference/keywords/is.md) pour déterminer si un objet fournit une implémentation de <xref:System.IFormatProvider> et teste si l’objet est `null`. Il utilise également le modèle d’élément ignoré pour gérer les objets non null de n’importe quel autre type.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Appels à des méthodes avec des paramètres out

Quand vous appelez la méthode `Deconstruct` pour déconstruire un type défini par l’utilisateur (une instance d’une classe, d’une structure ou d’une interface), vous pouvez ignorer les valeurs d’arguments `out` individuels. Vous pouvez cependant aussi ignorer la valeur d’arguments `out` lors de l’appel de n’importe quelle méthode avec un paramètre out.

L’exemple suivant appelle la méthode [DateTime.TryParse (String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) pour déterminer si la représentation sous forme de chaîne d’une date est valide dans la culture actuelle. Comme l’exemple concerne ici uniquement la validation de la chaîne de date et pas son analyse pour extraire la date, l’argument `out` de la méthode est un élément ignoré.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Élément ignoré autonome

Vous pouvez utiliser un élément ignoré autonome pour indiquer une variable que vous choisissez d’ignorer. L’exemple suivant utilise un élément ignoré autonome pour ignorer l’objet <xref:System.Threading.Tasks.Task> retourné par une opération asynchrone. Ceci a pour effet de supprimer l’exception levée par l’opération au moment où elle se termine.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Notez que `_` est aussi un identificateur valide. Quand il est utilisé en dehors d’un contexte pris en charge, `_` est traité non pas comme élément ignoré, mais comme variable valide. Si un identificateur nommé `_` est déjà dans l’étendue, l’utilisation de `_` comme élément ignoré autonome peut provoquer :

- Une modification accidentelle de la valeur de la variable `_` dans l’étendue en lui affectant la valeur de l’élément ignoré prévu. Par exemple :

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Une erreur de compilateur pour violation de sécurité du type. Par exemple :

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Erreur du compilateur CS0136 : « Impossible de déclarer une variable locale ou un paramètre nommé ‘\_’ dans cette portée, car ce nom est utilisé dans une portée locale englobante pour définir une variable locale ou un paramètre. » Par exemple :

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Déconstruction de tuples et autres types](deconstruct.md)
- [`is`Mot-clé](language-reference/keywords/is.md)
- [`switch`Mot-clé](language-reference/keywords/switch.md)
