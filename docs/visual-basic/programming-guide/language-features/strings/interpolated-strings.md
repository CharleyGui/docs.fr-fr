---
title: Chaînes interpolées
ms.date: 10/31/2017
ms.openlocfilehash: c427b48ce58a59ff3878f24f1989db6ac8c8239a
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805276"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Chaînes interpolées (référence Visual Basic)

Permettent de construire des chaînes.  Une chaîne interpolée ressemble à une chaîne de modèle contenant des *expressions interpolées*.  Une chaîne interpolée retourne une chaîne qui remplace les expressions interpolées qu’elle contient par leur représentation sous forme de chaîne. Cette fonctionnalité est disponible dans Visual Basic 14 et versions ultérieures.

Les arguments d’une chaîne interpolée sont plus faciles à comprendre qu’une [chaîne de format composite](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Par exemple, la chaîne interpolée

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

contient deux expressions interpolées, ’{name}’ et ’{hours:hh}’. La chaîne de format composite équivalente est la suivante :

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

La structure d’une chaîne interpolée est :

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

où :

- *field-width* est un entier signé qui indique le nombre de caractères du champ. S’il est positif, le champ est aligné à droite ; s’il est négatif, il est aligné à gauche.

- *format-string* est une chaîne de format qui convient au type d’objet mis en forme. Par exemple, pour une <xref:System.DateTime> valeur, il peut s’agir d’une [chaîne de format de date et d’heure standard](../../../../standard/base-types/standard-date-and-time-format-strings.md) telle que « d » ou « d ».

> [!IMPORTANT]
> N’ajoutez pas d’espace blanc entre les signes `$` et `"` au début de la chaîne. Cela provoque une erreur du compilateur.

Vous pouvez utiliser une chaîne interpolée partout où vous pouvez utiliser un littéral de chaîne.  La chaîne interpolée est évaluée à chaque exécution du code contenant la chaîne interpolée. Cela vous permet de séparer la définition et l’évaluation d’une chaîne interpolée.

Pour ajouter une accolade ("{" ou "}") dans une chaîne interpolée, utilisez deux accolades "{{" ou "}}".  Pour plus d’informations, consultez la section « Conversions implicites ».

Si la chaîne interpolée contient d’autres caractères ayant une signification particulière dans une chaîne interpolée, comme le guillemet ("), les deux-points (:) ou la virgule (,), ils doivent être échappés s’ils se trouvent dans du texte littéral, ou être inclus dans une expression délimitée par des parenthèses s’ils s’agit d’éléments de langage inclus dans une expression interpolée. L’exemple suivant échappe les guillemets pour les inclure dans la chaîne de résultat :

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Conversions implicites

Trois conversions de type implicite sont possibles à partir d’une chaîne interpolée :

1. La conversion d’une chaîne interpolée en un <xref:System.String>. L’exemple suivant retourne une chaîne dont les expressions de chaîne interpolée ont été remplacées par leur représentation sous forme de chaîne. Par exemple :

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Il s’agit du résultat final d’une interprétation de chaîne. Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont converties en une seule accolade.

2. La conversion d’une chaîne interpolée en variable <xref:System.IFormattable> qui permet de créer plusieurs chaînes de résultats avec un contenu spécifique de la culture, à partir d’une seule instance <xref:System.IFormattable>. Ce type de conversion est utile pour inclure des éléments, tels que les formats numériques et les formats de date adaptés à une culture.  Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées tant que vous ne mettez pas en forme la chaîne en appelant explicitement ou implicitement la méthode <xref:System.Object.ToString>.  Toutes les expressions d’interpolation contenues sont converties en {0} , {1} , et ainsi de suite.

   L’exemple suivant utilise la réflexion pour afficher les membres ainsi que les valeurs de champ et de propriété d’une variable <xref:System.IFormattable> créée à partir d’une chaîne interpolée. Il passe également la variable <xref:System.IFormattable> à la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Notez que la chaîne interpolée ne peut être inspectée qu’à l’aide de la réflexion. Si elle est passée à une méthode de mise en forme de chaîne, telle que <xref:System.Console.WriteLine(System.String)>, ses éléments de mise en forme sont résolus et la chaîne de résultat est retournée.

3. Conversion d’une chaîne interpolée en une <xref:System.FormattableString> variable qui représente une chaîne de format composite. L’inspection de la chaîne de format composite et de son rendu sous forme de chaîne de résultat, peut, par exemple, vous aider à réduire les risques d’attaque par injection pendant la création d’une requête. Un <xref:System.FormattableString> comprend également les éléments suivants :

      - Une surcharge <xref:System.FormattableString.ToString> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.CurrentCulture>.

      - <xref:System.FormattableString.Invariant%2A>Méthode qui produit une chaîne pour <xref:System.Globalization.CultureInfo.InvariantCulture> .

      - Une méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> qui produit une chaîne de résultat pour une culture spécifiée.

    Toutes les occurrences d’accolades doubles (« {{ » et « }} ») sont conservées sous la forme d’accolades doubles jusqu’à ce que vous le formatiez.  Toutes les expressions d’interpolation contenues sont converties en {0} , {1} , et ainsi de suite.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Informations de référence sur le langage Visual Basic](index.md)
