---
title: Utiliser les types d’enregistrements-didacticiel C#
description: Découvrez comment utiliser les types d’enregistrements, créer des hiérarchies d’enregistrements et quand choisir des enregistrements sur des classes.
ms.date: 11/12/2020
ms.openlocfilehash: 8a2cb6966ab4f93432723fd6f82618efa86b26aa
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688586"
---
# <a name="create-record-types"></a>Créer des types d’enregistrements

C# 9 introduit les *enregistrements*, un nouveau type de référence que vous pouvez créer à la place des classes ou des structs. Les enregistrements sont distincts des classes dans les types d’enregistrements utilisant l' *égalité basée sur les valeurs*. Deux variables d’un type d’enregistrement sont égales si les définitions de type d’enregistrement sont identiques et, si pour chaque champ, les valeurs des deux enregistrements sont égales. Deux variables d’un type de classe sont égales si les objets référencés sont du même type de classe et que les variables font référence au même objet. L’égalité basée sur la valeur implique d’autres fonctionnalités que vous souhaiterez probablement dans les types d’enregistrements. Le compilateur génère un grand nombre de ces membres lorsque vous déclarez un `record` au lieu d’un `class` .

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Déterminez si vous devez déclarer un `class` ou un `record` .
> - Déclarez les types d’enregistrements et les types d’enregistrements positionnels.
> - Remplacez les méthodes générées par le compilateur dans les enregistrements par vos méthodes.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET 5 ou une version ultérieure, y compris le compilateur C# 9,0 ou version ultérieure. Le compilateur C# 9,0 est disponible à partir de [Visual Studio 2019 version 16,8](https://visualstudio.microsoft.com/vs) ou du [Kit de développement logiciel (SDK) .net 5,0](https://dotnet.microsoft.com/download).

## <a name="characteristics-of-records"></a>Caractéristiques des enregistrements

Vous définissez un *enregistrement* en déclarant un type avec le `record` mot clé, au lieu du `class` `struct` mot clé ou. Un enregistrement est un type référence et suit la sémantique d’égalité basée sur les valeurs. Pour appliquer la sémantique de valeur, le compilateur génère plusieurs méthodes pour votre type d’enregistrement :

- Substitution de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> .
- Méthode virtuelle `Equals` dont le paramètre est le type d’enregistrement.
- Substitution de <xref:System.Object.GetHashCode?displayProperty=nameWithType> .
- Méthodes pour `operator ==` et `operator !=` .
- Les types d’enregistrements implémentent <xref:System.IEquatable%601?displayProperty=nameWithType> .

En outre, les enregistrements fournissent une substitution de <xref:System.Object.ToString?displayProperty=nameWithType> . Le compilateur synthétise les méthodes pour afficher les enregistrements à l’aide de <xref:System.Object.ToString?displayProperty=nameWithType> . Vous allez explorer ces membres au fur et à mesure que vous écrirez le code pour ce didacticiel. Enregistre les `with` expressions de prise en charge pour permettre une mutation non destructrice des enregistrements.

Vous pouvez également déclarer des *enregistrements positionnels* à l’aide d’une syntaxe plus concise. Le compilateur synthétise davantage de méthodes lorsque vous déclarez des enregistrements positionnels :

- Constructeur principal dont les paramètres correspondent aux paramètres positionnels de la déclaration d’enregistrement.
- Propriétés public init-only pour chaque paramètre d’un constructeur principal.
- `Deconstruct`Méthode permettant d’extraire des propriétés de l’enregistrement.

## <a name="build-temperature-data"></a>Données de température de build

Les données et les statistiques font partie des scénarios dans lesquels vous souhaiterez utiliser des enregistrements. Pour ce didacticiel, vous allez créer une application qui calcule le *degré de jours* pour différentes utilisations. Les *jours de degré* sont une mesure de chaleur (ou de l’absence de chaleur) sur une période de jours, de semaines ou de mois. Degré de suivi et prédiction de l’utilisation de l’énergie. Plus de plus chaud jours signifie plus de climatisation, et plus de jours plus froids signifient une utilisation plus grande du four. Degree Days aident à gérer les populations d’usines. Les jours sont corrélés à la croissance de la plante au fur et à mesure que les saisons évoluent. Le degree Days aide à effectuer le suivi des migrations animales pour les espèces qui voyagent pour correspondre au climat.

La formule est basée sur la température moyenne d’un jour donné et sur une température de ligne de base. Pour calculer le degré des jours dans le temps, vous avez besoin des températures haute et basse chaque jour pendant une période donnée. Commençons par créer une nouvelle application. Créez une nouvelle application console. Créez un nouveau type d’enregistrement dans un nouveau fichier nommé « DailyTemperature.cs » :

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DailyRecord":::

Le code précédent définit un *enregistrement positionnel*. Vous avez créé un type référence qui contient deux propriétés : `HighTemp` , et `LowTemp` . Ces propriétés sont des *Propriétés init uniquement*, ce qui signifie qu’elles peuvent être définies dans le constructeur ou à l’aide d’un initialiseur de propriété. Le `DailyTemperature` type a également un *constructeur principal* qui a deux paramètres qui correspondent aux deux propriétés. Vous utilisez le constructeur principal pour initialiser un `DailyTemperature` enregistrement :

:::code language="csharp" source="snippets/record-types/Program.cs" ID="DeclareData":::

Vous pouvez ajouter vos propres propriétés ou méthodes à des enregistrements, y compris des enregistrements positionnels. Vous devez calculer la température moyenne pour chaque jour. Vous pouvez ajouter cette propriété à l' `DailyTemperature` enregistrement :

:::code language="csharp" source="snippets/record-types/DailyTemperature.cs" ID="TemperatureRecord":::

Vérifions que vous pouvez utiliser ces données. Ajoutez le code suivant à votre méthode `Main` :

```csharp
foreach (var item in data)
    Console.WriteLine(item);
```

Exécutez votre application. vous verrez une sortie similaire à l’affichage suivant (plusieurs lignes supprimées pour l’espace) :

```dotnetcli
DailyTemperature { HighTemp = 57, LowTemp = 30, Mean = 43.5 }
DailyTemperature { HighTemp = 60, LowTemp = 35, Mean = 47.5 }


DailyTemperature { HighTemp = 80, LowTemp = 60, Mean = 70 }
DailyTemperature { HighTemp = 85, LowTemp = 66, Mean = 75.5 }
```

Le code précédent montre la sortie de la substitution de `ToString` synthétisé par le compilateur. Si vous préférez du texte différent, vous pouvez écrire votre propre version de `ToString` . Cela empêche le compilateur de synthétiser une version pour vous.

## <a name="compute-degree-days"></a>Degré de calcul en jours

Pour calculer les jours, vous prenez la différence par rapport à une température de référence et la température moyenne d’un jour donné. Pour mesurer la chaleur dans le temps, vous supprimez tous les jours où la température moyenne est inférieure à la ligne de base. Pour mesurer le froid au fil du temps, vous devez ignorer les jours où la température moyenne est supérieure à la ligne de base. Par exemple, les États-Unis utilisent 65F comme base pour les jours de chauffage et de refroidissement. Il s’agit de la température à laquelle aucun chauffage ou refroidissement n’est nécessaire. Si un jour a une température moyenne de 70F, ce jour est de 5 jours de refroidissement et 0 jour de chauffage. À l’inverse, si la température moyenne est 55F, ce jour correspond à 10 jours de chauffage et 0 jour de refroidissement.

Vous pouvez exprimer ces formules sous la forme d’une petite hiérarchie de types d’enregistrements : un type de jour abstrait et deux types concrets pour le chauffage des jours et le degré de refroidissement. Ces types peuvent également être des enregistrements positionnels. Ils prennent une température de référence et une séquence d’enregistrements de température quotidiens comme arguments pour le constructeur principal :

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DegreeDaysRecords":::

L' `DegreeDays` enregistrement abstrait est la classe de base partagée pour les `HeatingDegreeDays` `CoolingDegreeDays` enregistrements et. Les déclarations de constructeur principales sur les enregistrements dérivés montrent comment gérer l’initialisation des enregistrements de base. Votre enregistrement dérivé déclare des paramètres pour tous les paramètres dans le constructeur principal d’enregistrement de base. L’enregistrement de base déclare et initialise ces propriétés. L’enregistrement dérivé ne les masque pas, mais crée et initialise uniquement les propriétés des paramètres qui ne sont pas déclarés dans son enregistrement de base. Dans cet exemple, les enregistrements dérivés n’ajoutent pas de nouveaux paramètres de constructeur principal. Testez votre code en ajoutant le code suivant à votre `Main` méthode :

:::code language="csharp" source="snippets/record-types/Program.cs" ID="HeatingAndCooling":::

Vous obtenez une sortie similaire à l’affichage suivant :

```dotnetcli
HeatingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 85 }
CoolingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 71.5 }
```

## <a name="define-compiler-synthesized-methods"></a>Définir des méthodes synthétisées par le compilateur

Votre code calcule le nombre correct de jours de chauffage et de refroidissement pendant cette période. Mais cet exemple montre pourquoi vous souhaiterez peut-être remplacer certaines des méthodes synthétisées pour les enregistrements. Vous pouvez déclarer votre propre version de l’une des méthodes synthétisées par le compilateur dans un type d’enregistrement, à l’exception de la méthode Clone. La méthode Clone a un nom généré par le compilateur et vous ne pouvez pas fournir une implémentation différente. Ces méthodes synthétisées incluent un constructeur de copie, les membres de l' <xref:System.IEquatable%601?displayProperty=nameWithType> interface, les tests d’égalité et d’inégalité, et <xref:System.Object.GetHashCode> . À cet effet, vous allez synthétiser `PrintMembers` . Vous pouvez également déclarer votre propre `ToString` , mais `PrintMembers` offre une meilleure option pour les scénarios d’héritage. Pour fournir votre propre version d’une méthode synthétisée, la signature doit correspondre à la méthode synthétisée.

L' `TempRecords` élément dans la sortie de la console n’est pas utile. Elle affiche le type, mais rien d’autre. Vous pouvez modifier ce comportement en fournissant votre propre implémentation de la méthode synthétisée `PrintMembers` . La signature dépend des modificateurs appliqués à la `record` déclaration :

- Si un type d’enregistrement est `sealed` , la signature est `private bool PrintMembers(StringBuilder builder);`
- Si un type d’enregistrement n’est pas `sealed` et dérive de `object` (c’est-à-dire qu’il ne déclare pas d’enregistrement de base), la signature est `protected virtual bool PrintMembers(StringBuilder builder);`
- Si un type d’enregistrement n’est pas `sealed` et qu’il dérive d’un autre enregistrement, la signature est `protected override bool PrintMembers(StringBuilder builder);`

Ces règles sont plus faciles à comprendre pour comprendre l’objectif de `PrintMembers` . `PrintMembers` ajoute à une chaîne des informations sur chaque propriété d’un type d’enregistrement. Le contrat requiert des enregistrements de base pour ajouter leurs membres à l’affichage et suppose que les membres dérivés ajouteront leurs membres. Chaque type d’enregistrement synthétise un `ToString` remplacement qui ressemble à l’exemple suivant pour `HeatingDegreeDays` :

```csharp
public override string ToString()
{
    StringBuilder stringBuilder = new StringBuilder();
    stringBuilder.Append("HeatingDegreeDays");
    stringBuilder.Append(" { ");
    if (PrintMembers(stringBuilder))
    {
        stringBuilder.Append(" ");
    }
    stringBuilder.Append("}");
    return stringBuilder.ToString();
}
```

Vous déclarez une `PrintMembers` méthode dans l' `DegreeDays` enregistrement qui n’imprime pas le type de la collection :

:::code language="csharp" source="snippets/record-types/DegreeDays.cs" ID="AddPrintMembers":::

La signature déclare une `virtual protected` méthode pour qu’elle corresponde à la version du compilateur. Ne vous inquiétez pas si vous recevez les accesseurs erronés ; le langage applique la signature correcte. Si vous oubliez les modificateurs corrects pour toute méthode synthétisée, le compilateur émet des avertissements ou des erreurs qui vous aident à obtenir la signature appropriée.

## <a name="non-destructive-mutation"></a>Mutation non destructrice

Les membres synthétisés dans un enregistrement positionnel ne modifient pas l’état de l’enregistrement. L’objectif est que vous pouvez créer plus facilement des enregistrements immuables. Examinez à nouveau les déclarations précédentes pour `HeatingDegreeDays` et `CoolingDegreeDays` . Les membres ajoutés effectuent des calculs sur les valeurs de l’enregistrement, mais ne changent pas d’État. Les enregistrements positionnels facilitent la création de types référence immuables.

La création de types référence immuables signifie que vous souhaiterez utiliser une mutation non destructrice. Vous créez des instances d’enregistrement similaires aux instances d’enregistrement existantes à l’aide d' [ `with` expressions](../../language-reference/operators/with-expression.md). Ces expressions sont une construction de copie avec des affectations supplémentaires qui modifient la copie. Le résultat est une nouvelle instance d’enregistrement dans laquelle chaque propriété a été copiée à partir de l’enregistrement existant et éventuellement modifiée. L’enregistrement d’origine est inchangé.

Nous allons ajouter quelques fonctionnalités à votre programme qui illustrent des `with` expressions. Tout d’abord, nous allons créer un nouvel enregistrement pour calculer le nombre de jours croissants à l’aide des mêmes données. Le nombre de *jours croissants* utilise généralement 41F comme ligne de base et mesure les températures au-dessus de la ligne de base. Pour utiliser les mêmes données, vous pouvez créer un nouvel enregistrement similaire à `coolingDegreeDays` , mais avec une température de base différente :

:::code language="csharp" source="snippets/record-types/Program.cs" ID="GrowingDegreeDays":::

Vous pouvez comparer le nombre de degrés calculés aux nombres générés à l’aide d’une température de référence supérieure. N’oubliez pas que les enregistrements sont des *types référence* et que ces copies sont des copies superficielles. Le tableau des données n’est pas copié, mais les deux enregistrements font référence aux mêmes données. Ce fait est un avantage dans un autre scénario. Pour des jours de plus en bout, il est utile d’effectuer le suivi du total des 5 jours précédents. Vous pouvez créer des enregistrements avec différentes données sources à l’aide d' `with` expressions. Le code suivant génère une collection de ces accumulations, puis affiche les valeurs :

:::code language="csharp" source="snippets/record-types/Program.cs" ID="RunningFiveDayTotal":::

Vous pouvez également utiliser `with` des expressions pour créer des copies d’enregistrements. Ne spécifiez aucune propriété entre les accolades de l' `with` expression. Cela signifie créer une copie et ne pas modifier les propriétés :

```csharp
var growingDegreeDaysCopy = growingDegreeDays with { };
```

Exécutez l’application finie pour afficher les résultats.

## <a name="summary"></a>Résumé

Ce didacticiel a présenté plusieurs aspects des enregistrements. Les enregistrements fournissent une syntaxe concise pour les types de référence où l’utilisation fondamentale est le stockage des données. Pour les classes orientées objet, l’utilisation fondamentale est la définition des responsabilités. Ce didacticiel se concentre sur les *enregistrements positionnels*, où vous pouvez utiliser une syntaxe concise pour déclarer les propriétés d’initialisation uniquement pour un enregistrement. Le compilateur synthétise plusieurs membres de l’enregistrement pour copier et comparer des enregistrements. Vous pouvez ajouter tous les autres membres dont vous avez besoin pour vos types d’enregistrements. Vous pouvez créer des types d’enregistrements immuables sachant qu’aucun des membres générés par le compilateur ne fera passer l’État. Pour les enregistrements positionnels, les expressions facilitent la `with` prise en charge de la mutation non destructrice.

Les enregistrements ajoutent une autre façon de définir des types. `class`Les définitions vous permettent de créer des hiérarchies orientées objet qui se concentrent sur les responsabilités et le comportement des objets. Vous créez `struct` des types pour les structures de données qui stockent les données et sont suffisamment petits pour être copiés efficacement. Vous créez des enregistrements lorsque vous souhaitez une comparaison et une égalité basée sur les valeurs, que vous ne voulez pas copier de valeurs et que vous souhaitez utiliser des variables de référence.

Vous pouvez apprendre la description complète des enregistrements en lisant la [spécification de type d’enregistrement proposé](~/_csharplang/proposals/csharp-9.0/records.md).
