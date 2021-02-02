---
title: Éléments ignorés - Guide C#
description: Décrit la prise en charge par C# des éléments ignorés, qui sont des variables qui peuvent être ignorées, et les différentes façons dont les éléments ignorés peuvent être utilisés.
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: 7562da880ff3136dfc04ce4061bafa8ed55f5a23
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99426916"
---
# <a name="discards---c-guide"></a>Éléments ignorés - Guide C#

À compter de C# 7,0, C# prend en charge les éléments ignorés, qui sont des variables d’espace réservé qui sont intentionnellement inutilisées dans le code de l’application. Les éléments ignorés sont équivalents aux variables non affectées ; ils n’ont pas de valeur. Un abandon communique l’intention au compilateur et d’autres personnes qui lisent votre code : vous avez prévu d’ignorer le résultat d’une expression. Vous pouvez ignorer le résultat d’une expression, d’un ou de plusieurs membres d’une expression de tuple, d’un `out` paramètre d’une méthode ou de la cible d’une expression de critères spéciaux.

Étant donné qu’il n’y a qu’une seule variable à rejet, cette variable ne peut même pas être allouée au stockage. Les éléments ignorés peuvent réduire les allocations de mémoire. Les éléments ignorés rendent l’objectif de votre code clair. Ils améliorent la lisibilité et la maintenabilité.

Vous indiquez qu’une variable est un élément ignoré en lui affectant comme nom le trait de soulignement (`_`). Par exemple, l’appel de méthode suivant retourne un tuple dans lequel les première et deuxième valeurs sont ignorées. `area` est une variable déclarée précédemment définie sur le troisième composant retourné par `GetCityInformation` :

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

À compter de C# 9,0, vous pouvez utiliser des éléments ignorés pour spécifier les paramètres d’entrée inutilisés d’une expression lambda. Pour plus d’informations, consultez la section [paramètres d’entrée d’une expression lambda](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) de l’article [expressions lambda](language-reference/operators/lambda-expressions.md) .

Lorsque `_` est un ignore valide, toute tentative de récupération de sa valeur ou son utilisation dans une opération d’assignation génère l’erreur de compilateur CS0301, « le nom' \_ 'n’existe pas dans le contexte actuel ». Cette erreur est due `_` au fait qu’une valeur n’est pas affectée à et peut même ne pas être affectée à un emplacement de stockage. S’il s’agit d’une variable réelle, vous ne pouviez pas ignorer plus d’une valeur, comme le faisait l’exemple précédent.

## <a name="tuple-and-object-deconstruction"></a>Déconstruction de tuple et d’objet

Les éléments ignorés sont utiles lors de l’utilisation de tuples lorsque votre code d’application utilise des éléments tuples, mais en ignore d’autres. Par exemple, la `QueryCityDataForYears` méthode suivante retourne un tuple avec le nom d’une ville, sa zone, une année, la population de la ville pour cette année, une seconde année et la population de la ville pour cette seconde année. L’exemple montre la différence de population entre ces deux années. Parmi les données disponibles dans le tuple, nous ne sommes pas intéressés par la région de la ville, et nous connaissons le nom de la ville et les deux dates au moment du design. Par conséquent, nous sommes intéressés seulement par les deux valeurs de la population stockées dans le tuple et nous pouvons gérer ses valeurs restantes comme éléments ignorés.  

:::code language="csharp" source="snippets/discards/discard-tuple.cs" ID="DiscardTupleMember" :::

Pour plus d’informations sur la déconstruction de tuples avec des éléments ignorés, consultez [Déconstruction de tuples et d’autres types](deconstruct.md#deconstructing-tuple-elements-with-discards).

La méthode `Deconstruct` d’une classe, d’un struct ou d’une interface vous permet aussi de récupérer et de déconstruire un ensemble spécifique de données d’un objet. Vous pouvez utiliser des éléments ignorés lorsque vous êtes intéressé par l’utilisation d’un seul sous-ensemble des valeurs déconstruites. L’exemple suivant déconstruit un objet `Person` en quatre chaînes (le prénom, le nom, la ville et l’État), mais ignore le nom et l’État.

:::code language="csharp" source="snippets/discards/discard-class.cs" :::

Pour plus d’informations sur la déconstruction de types définis par l’utilisateur avec des éléments ignorés, consultez [Déconstruction de tuples et d’autres types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch"></a>Critères spéciaux avec « switch »

Le *modèle d’abandon* peut être utilisé dans les critères spéciaux avec le mot clé [switch](language-reference/keywords/switch.md) . Chaque expression correspond toujours au modèle d’élément ignoré. (Il peut être utilisé avec des expressions [is](language-reference/keywords/is.md) . Toutefois, cette utilisation est rare, car elle peut être supprimée sans changer sa signification).

L’exemple suivant définit une méthode `ProvidesFormatInfo` qui utilise des instructions [is](language-reference/keywords/is.md) pour déterminer si un objet fournit une implémentation de <xref:System.IFormatProvider> et teste si l’objet est `null`. Il utilise également le modèle d’élément ignoré pour gérer les objets non null de n’importe quel autre type.

:::code language="csharp" source="snippets/discards/discard-pattern2.cs" ID="DiscardSwitchExample" :::

## <a name="calls-to-methods-with-out-parameters"></a>Appels à des méthodes avec des `out` paramètres

Quand vous appelez la méthode `Deconstruct` pour déconstruire un type défini par l’utilisateur (une instance d’une classe, d’une structure ou d’une interface), vous pouvez ignorer les valeurs d’arguments `out` individuels. Toutefois, vous pouvez également ignorer la valeur des `out` arguments lors de l’appel d’une méthode avec un `out` paramètre.

L’exemple suivant appelle la méthode [DateTime.TryParse (String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) pour déterminer si la représentation sous forme de chaîne d’une date est valide dans la culture actuelle. Comme l’exemple concerne ici uniquement la validation de la chaîne de date et pas son analyse pour extraire la date, l’argument `out` de la méthode est un élément ignoré.

:::code language="csharp" source="snippets/discards/discard-out1.cs" ID="DiscardOutParameter" :::

## <a name="a-standalone-discard"></a>Élément ignoré autonome

Vous pouvez utiliser un élément ignoré autonome pour indiquer une variable que vous choisissez d’ignorer. Une utilisation classique consiste à utiliser une assignation pour garantir qu’un argument n’a pas la valeur null. Le code suivant utilise un ignore pour forcer une assignation. La partie droite de l’assignation utilise l' [opérateur de fusion Null](language-reference/operators/null-coalescing-operator.md) pour lever une <xref:System.ArgumentNullException?displayProperty=nameWithType> lorsque l’argument a la valeur `null` . Le code n’a pas besoin du résultat de l’assignation. il est donc ignoré. L’expression force une vérification de valeur null. L’abandon clarifie votre intention : le résultat de l’assignation n’est pas nécessaire ou utilisé.

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="ArgNullCheck" :::

L’exemple suivant utilise un élément ignoré autonome pour ignorer l’objet <xref:System.Threading.Tasks.Task> retourné par une opération asynchrone. L’assignation de la tâche a pour effet de supprimer l’exception levée par l’opération, car elle est sur le paragraphe de se terminer. L’objectif est clair : vous voulez ignorer le `Task` et ignorer les erreurs générées à partir de cette opération asynchrone.

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetDiscardTask" :::

Sans affecter la tâche à un ignore, le code suivant génère un avertissement du compilateur :

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetNoDiscardTask" :::

> [!NOTE]
> Si vous exécutez l’un des deux exemples précédents à l’aide d’un débogueur, le débogueur arrêtera le programme quand l’exception sera levée. Si le débogueur n’est pas attaché, l’exception est ignorée silencieusement dans les deux cas.

`_` est également un identificateur valide. Quand il est utilisé en dehors d’un contexte pris en charge, `_` est traité non pas comme élément ignoré, mais comme variable valide. Si un identificateur nommé `_` est déjà dans l’étendue, l’utilisation de `_` comme élément ignoré autonome peut provoquer :

- Une modification accidentelle de la valeur de la variable `_` dans l’étendue en lui affectant la valeur de l’élément ignoré prévu. Par exemple :
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableIdentifier" :::
- Une erreur de compilateur pour violation de sécurité du type. Par exemple :
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableTypeInference" :::
- Erreur du compilateur CS0136 : « Impossible de déclarer une variable locale ou un paramètre nommé ‘\_’ dans cette portée, car ce nom est utilisé dans une portée locale englobante pour définir une variable locale ou un paramètre. » Par exemple :
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="CannotRedeclare" :::

## <a name="see-also"></a>Voir aussi

- [Déconstruction de tuples et d’autres types](deconstruct.md)
- [`is` mot](language-reference/keywords/is.md)
- [`switch` mot](language-reference/keywords/switch.md)
