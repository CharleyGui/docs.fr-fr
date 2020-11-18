---
title: Meilleures pratiques pour l’affichage et la persistance des données mises en forme dans .NET
description: Apprenez à afficher et à conserver efficacement des données numériques et de date dans les applications .NET.
ms.date: 05/01/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1748363089a80538a19e91b1955fe9257de39a4e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825141"
---
# <a name="best-practices-for-displaying-and-persisting-formatted-data"></a>Meilleures pratiques pour l’affichage et la persistance des données mises en forme

Cet article examine comment les données mises en forme, telles que les données numériques et les données de date et d’heure, sont traitées pour l’affichage et le stockage.

Lorsque vous développez avec .NET, utilisez la mise en forme dépendante de la culture pour afficher des données autres que des chaînes, telles que des nombres et des dates, dans une interface utilisateur. Utilisez la mise en forme avec la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture) pour conserver les données qui ne sont pas des chaînes sous forme de chaîne. N’utilisez pas la mise en forme dépendante de la culture pour rendre des données numériques ou de date et d’heure sous forme de chaîne.

## <a name="displaying-formatted-data"></a>Affichage des données mises en forme

Lorsque vous affichez des données non-chaînées telles que les nombres et les dates et heures aux utilisateurs, mettez-les en forme en utilisant les paramètres de la culture de l'utilisateur. Par défaut, tous les éléments suivants utilisent la culture du thread actuelle dans les opérations de mise en forme :

- Chaînes interpolées prises en charge par les compilateurs [C#](../../csharp/language-reference/tokens/interpolated.md) et [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).
- Opérations de concaténation de chaîne qui utilisent les opérateurs de concaténation [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) ou [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md), ou qui appellent directement la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>.
- Méthode <xref:System.String.Format%2A?displayProperty=nameWithType>
- Méthodes `ToString` des types numériques et des types de date et d’heure.

Pour spécifier explicitement qu’une chaîne doit être mise en forme en utilisant les conventions d’une culture désignée ou de la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture), vous pouvez procéder comme suit :

- Quand vous utilisez les méthodes <xref:System.String.Format%2A?displayProperty=nameWithType> et `ToString`, appelez une surcharge qui a un paramètre `provider`, tel que <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ou <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> et passez-lui la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, une instance <xref:System.Globalization.CultureInfo> qui représente la culture souhaitée, ou la propriété <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.

- Pour la concaténation de chaîne, n’autorisez pas le compilateur à effectuer de conversions implicites. Au lieu de cela, effectuez une conversion explicite en appelant une surcharge `ToString` ayant un paramètre `provider`. Par exemple, le compilateur utilise implicitement la culture actuelle lors de la conversion <xref:System.Double> d’une valeur en une chaîne dans le code suivant :

  [!code-csharp[Implicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#1)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#1)]

  Au lieu de cela, vous pouvez spécifier explicitement la culture dont les conventions de mise en forme sont utilisées lors de la conversion en appelant la <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> méthode, comme le montre le code suivant :

  [!code-csharp[Explicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#2)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#2)]

- Pour l’interpolation de chaîne, plutôt que d’affecter une chaîne interpolée à une instance <xref:System.String>, affectez-la à un élément <xref:System.FormattableString>. Vous pouvez ensuite appeler sa méthode <xref:System.FormattableString.ToString?displayProperty=nameWithType> pour produire une chaîne de résultat qui reflète les conventions de la culture actuelle, ou vous pouvez appeler la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> pour produire une chaîne de résultat qui reflète les conventions d’une culture spécifiée. Vous pouvez également transmettre la chaîne pouvant être mise en forme à la méthode <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> statique pour produire une chaîne de résultat qui reflète les conventions de la culture invariante. L'exemple suivant illustre cette approche. (La sortie de l’exemple correspond à la culture actuelle en-US.)

  [!code-csharp[String interpolation](./snippets/best-practices-strings/csharp/formattable/Program.cs)]
  [!code-vb[String interpolation](./snippets/best-practices-strings/vb/formattable/Program.vb)]

## <a name="persisting-formatted-data"></a>Persistance des données mises en forme

Vous pouvez rendre persistantes des données non-chaînées soit comme données binaires, soit comme données mises en forme. Si vous choisissez de l'enregistrer en tant que données mises en forme, vous devez appeler une surcharge de méthode de mise en forme qui inclut un paramètre `provider` et le passer à la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . La culture dite indifférente fournit un format cohérent pour les données mises en forme qui est indépendant de la culture et de l'ordinateur. En revanche, assurer la persistance de données mises en forme à l'aide de cultures autres que la culture dite indifférente a plusieurs limites :

- Les données seront vraisemblablement inutilisables si elles sont récupérées sur un système ayant une autre culture, ou si l'utilisateur du système actuel change la culture actuelle et essaie de récupérer les données.
- Les propriétés d'une culture sur un ordinateur spécifique peuvent différer des valeurs standard. À tout moment, un utilisateur peut personnaliser les paramètres d'affichage selon la culture. De ce fait, les données mises en forme sont stockées sur un système et peuvent ne pas être lisibles lorsque l'utilisateur personnalise les paramètres de culture. La portabilité des données mises en forme sur différents ordinateurs peut être encore plus limitée.
- Des normes internationales, régionales ou nationales qui régissent la mise en forme des nombres ou des dates et heures évoluent au fil du temps, et ces modifications sont intégrées dans les mises à jour du système d'exploitation Windows. Quand les conventions de mise en forme changent, les données qui ont été mises en forme en utilisant les conventions antérieures peuvent devenir illisibles.

L'exemple suivant illustre la portabilité limitée qui résulte de l'utilisation de la mise en forme qui tient compte de la culture pour assurer la persistance des données. L'exemple enregistre un tableau de valeurs de date et d'heure dans un fichier. Celles-ci sont mises en forme en utilisant les conventions culturelles de l'anglais (États-Unis). Une fois que l'application change la culture du thread actuel pour appliquer le français (Suisse), elle essaie de lire les valeurs enregistrées en utilisant les conventions de mise en forme de la culture actuelle. La tentative de lecture des éléments de données par deux fois renvoie une exception <xref:System.FormatException> , et le tableau de dates contient maintenant deux éléments incorrects qui sont identiques à <xref:System.DateTime.MinValue>.

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Toutefois, si vous remplacez la <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> propriété par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> dans les appels à <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> et <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> , les données de date et d’heure persistantes sont correctement restaurées, comme le montre la sortie suivante :

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```
