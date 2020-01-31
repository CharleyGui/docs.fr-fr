---
title: Prise en charge de DateTime et DateTimeOffset dans System.Text.Json
description: Vue d’ensemble de la façon dont les types DateTime et DateTimeOffset sont pris en charge dans la bibliothèque System. Text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: fb8836d9c556b317c50b6b34a9dde4e42c6486b5
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867345"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Prise en charge de DateTime et DateTimeOffset dans System.Text.Json

La bibliothèque System. Text. JSON analyse et écrit des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> en fonction du profil étendu ISO 8601 :-2019.
Les [convertisseurs](xref:System.Text.Json.Serialization.JsonConverter%601) fournissent une prise en charge personnalisée pour la sérialisation et la désérialisation avec <xref:System.Text.Json.JsonSerializer>.
La prise en charge personnalisée peut également être implémentée lors de l’utilisation de <xref:System.Text.Json.Utf8JsonReader> et <xref:System.Text.Json.Utf8JsonWriter>.

## <a name="support-for-the-iso-8601-12019-format"></a>Prise en charge du format ISO 8601-1:2019

Les types <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>et <xref:System.Text.Json.JsonElement> analysent et écrivent des représentations de <xref:System.DateTime> et de texte <xref:System.DateTimeOffset> en fonction du profil étendu du format ISO 8601-1:2019 ; par exemple, 2019-07-26T16:59:57-05:00.

les données <xref:System.DateTime> et <xref:System.DateTimeOffset> peuvent être sérialisées avec <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Elles peuvent également être désérialisées avec <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Avec les options par défaut, les <xref:System.DateTime> d’entrée et les représentations textuelles <xref:System.DateTimeOffset> doivent être conformes au profil ISO 8601-1:2019 étendu.
Si vous tentez de désérialiser des représentations qui ne sont pas conformes au profil, <xref:System.Text.Json.JsonSerializer> lèveront une <xref:System.Text.Json.JsonException>:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

L' <xref:System.Text.Json.JsonDocument> fournit un accès structuré au contenu d’une charge utile JSON, y compris les représentations <xref:System.DateTime> et <xref:System.DateTimeOffset>. L’exemple ci-dessous montre comment, lorsqu’une collection de températures est donnée, la température moyenne sur lundi peut être calculée :

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Si vous tentez de calculer la température moyenne en fonction d’une charge utile avec des représentations <xref:System.DateTime> non conformes, <xref:System.Text.Json.JsonDocument> lèvera une <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Le niveau inférieur <xref:System.Text.Json.Utf8JsonWriter> écrit des données <xref:System.DateTime> et <xref:System.DateTimeOffset> :

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> analyse les données de <xref:System.DateTime> et de <xref:System.DateTimeOffset> :

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Si vous tentez de lire des formats non conformes avec <xref:System.Text.Json.Utf8JsonReader>, il lèvera une <xref:System.FormatException>:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Prise en charge personnalisée pour <xref:System.DateTime> et <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Lors de l’utilisation de <xref:System.Text.Json.JsonSerializer>

Si vous souhaitez que le sérialiseur effectue une analyse personnalisée ou une mise en forme, vous pouvez implémenter des [convertisseurs personnalisés](xref:System.Text.Json.Serialization.JsonConverter%601).
Voici quelques exemples :

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Utilisation de `DateTime(Offset).Parse` et `DateTime(Offset).ToString`

Si vous ne pouvez pas déterminer les formats de vos <xref:System.DateTime> d’entrée ou <xref:System.DateTimeOffset> des représentations textuelles, vous pouvez utiliser la méthode `DateTime(Offset).Parse` dans la logique de lecture de votre convertisseur. Cela vous permet d’utiliser. Prise en charge étendue nette pour l’analyse de différents formats de texte <xref:System.DateTime> et <xref:System.DateTimeOffset>, y compris les chaînes non ISO 8601 et les formats ISO 8601 qui ne sont pas conformes au profil ISO 8601-1:2019 étendu. Cette approche est beaucoup moins performante que l’utilisation de l’implémentation native du sérialiseur.

Pour la sérialisation, vous pouvez utiliser la méthode `DateTime(Offset).ToString` dans votre logique d’écriture de convertisseur. Cela vous permet d’écrire des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> à l’aide de l’un des [formats de date et d’heure standard](../base-types/standard-date-and-time-format-strings.md), ainsi que des [formats de date et d’heure personnalisés](../base-types/custom-date-and-time-format-strings.md).
Cela est également beaucoup moins performant que l’utilisation de l’implémentation native du sérialiseur.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Lors de l’implémentation de <xref:System.Text.Json.Serialization.JsonConverter%601>, et `T` est <xref:System.DateTime>, le paramètre `typeToConvert` sera toujours `typeof(DateTime)`.
Le paramètre est utile pour gérer les cas polymorphes et lors de l’utilisation de génériques pour obtenir des `typeof(T)` de façon performante.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Utilisation de <xref:System.Buffers.Text.Utf8Parser> et <xref:System.Buffers.Text.Utf8Formatter>

Vous pouvez utiliser les méthodes d’analyse et de mise en forme rapides UTF-8 dans votre logique de conversion si votre <xref:System.DateTime> d’entrée ou <xref:System.DateTimeOffset> représentations de texte sont conformes avec l’une des [chaînes de format de date et d’heure standard](../base-types/standard-date-and-time-format-strings.md)"R", "l", "O" ou "G", ou si vous souhaitez écrire en fonction de l’un de ces formats. C’est beaucoup plus rapide que d’utiliser `DateTime(Offset).Parse` et `DateTime(Offset).ToString`.

Cet exemple montre un convertisseur personnalisé qui sérialise et désérialise <xref:System.DateTime> valeurs en fonction [du format standard « R »](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Le format standard « R » aura toujours une longueur de 29 caractères.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Utilisation de `DateTime(Offset).Parse` comme solution de secours pour l’analyse native du sérialiseur

Si vous vous attendez généralement à ce que votre <xref:System.DateTime> d’entrée ou <xref:System.DateTimeOffset> données soient conformes au profil ISO 8601-1:2019 étendu, vous pouvez utiliser la logique d’analyse native du sérialiseur. Vous pouvez également implémenter un mécanisme de secours uniquement dans le cas.
Cet exemple montre que, après l’échec de l’analyse d’une représentation de texte <xref:System.DateTime> à l’aide de <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, le convertisseur analyse correctement les données à l’aide de <xref:System.DateTime.Parse(System.String)>.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Lors de l’écriture avec <xref:System.Text.Json.Utf8JsonWriter>

Si vous souhaitez écrire une représentation <xref:System.DateTime> ou <xref:System.DateTimeOffset> textuelle personnalisée avec <xref:System.Text.Json.Utf8JsonWriter>, vous pouvez mettre en forme votre représentation personnalisée sur une <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`ou <xref:System.Text.Json.JsonEncodedText>, puis la passer à la méthode <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> correspondante.

L’exemple suivant montre comment créer un format de <xref:System.DateTime> personnalisé avec <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, puis écrit avec la méthode <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> :

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Lors de la lecture avec <xref:System.Text.Json.Utf8JsonReader>

Si vous souhaitez lire une <xref:System.DateTime> personnalisée ou <xref:System.DateTimeOffset> représentation textuelle avec <xref:System.Text.Json.Utf8JsonReader>, vous pouvez obtenir la valeur du jeton JSON actuel en tant que <xref:System.String> à l’aide de <xref:System.Text.Json.Utf8JsonReader.GetString>, puis analyser la valeur à l’aide d’une logique personnalisée.

L’exemple suivant montre comment récupérer une représentation textuelle de <xref:System.DateTimeOffset> personnalisée à l’aide d' <xref:System.Text.Json.Utf8JsonReader.GetString>, puis l’analyser à l’aide de <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Le profil ISO 8601-1:2019 étendu dans System. Text. JSON

### <a name="date-and-time-components"></a>Composants de date et d’heure

Le profil ISO 8601-1:2019 étendu implémenté dans <xref:System.Text.Json> définit les composants suivants pour les représentations de date et d’heure. Ces composants sont utilisés pour définir différents niveaux de granularité pris en charge lors de l’analyse et de la mise en forme des <xref:System.DateTime> et des représentations de <xref:System.DateTimeOffset>.

| Composant       | Format                      | Description                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Année            | "yyyy"                      | 0001-9999                                                                       |
| Mois           | "MM"                        | 01-12                                                                           |
| Jour             | "dd"                        | 01-28, 01-29, 01-30, 01-31 sur la base du mois/de l’année                                  |
| Heure            | "HH"                        | 00-23                                                                           |
| Minute          | "mm"                        | 00-59                                                                           |
| Seconde          | "ss"                        | 00-59                                                                           |
| Seconde fraction | "FFFFFFF"                   | Au minimum un chiffre, 16 chiffres au maximum                                      |
| Décalage horaire     | "K"                         | « Z » ou « ( » + « / »-« ) HH » : « mm »                                                |
| Temps partiel    | "HH" : 'mm' : 'ss [FFFFFFF] "     | Heure sans informations de décalage UTC                                             |
| Date complète       | « chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-yyyy'-'mm'-'dd »            | Date du calendrier                                                                   |
| Plein temps       | « Time’K partiel »           | Heure UTC du jour ou heure locale du jour avec le décalage horaire entre l’heure locale et l’heure UTC |
| Date et heure       | "'Date complète’t' « heure complète' » | Date et heure calendaires de la journée, par exemple 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Prise en charge de l’analyse

Les niveaux de granularité suivants sont définis pour l’analyse :

1. 'Date complète'
    1. « chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-yyyy'-'mm'-'dd »

2. "'Date complète’t' 'heure' ' : ' 'minute'
    1. « chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh » : « mm »

3. "'Date complète’t' 'temps partiel'"
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS' ([spécificateur de format pouvant être trié ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF

4. "'Date complète’t' 'heure heure' ' : ' 'minute' 'décalage horaire'"
    1. « chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh » : « mmZ »
    2. « chaîne-personnalisée "YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh » : « mm (' + '/'-') HH » : « mm »

5. « Date et heure »
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'ssZ'
    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFFZ"
    3. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS (' + '/'-') HH' : 'mm'
    4. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF (' + '/'-') HH' : 'mm'

S’il existe des fractions décimales pour les secondes, il doit y avoir au moins un chiffre ; `2019-07-26T00:00:00.` n’est pas autorisé.
Alors que jusqu’à 16 chiffres fractionnaires sont autorisés, seuls les sept premiers sont analysés. Tout au-delà de ce qui est considéré comme un zéro.
Par exemple, `2019-07-26T00:00:00.1234567890` sera analysé comme s’il s’agissait d' `2019-07-26T00:00:00.1234567`.
Cela permet de rester compatible avec l’implémentation de <xref:System.DateTime>, qui est limitée à cette résolution.

Les secondes bissextiles ne sont pas prises en charge.

### <a name="support-for-formatting"></a>Prise en charge de la mise en forme

Les niveaux de granularité suivants sont définis pour la mise en forme :

1. "'Date complète’t' 'temps partiel'"
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS' ([spécificateur de format pouvant être trié ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Utilisé pour mettre en forme une <xref:System.DateTime> sans fractions de seconde et sans informations de décalage.

    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF

        Utilisé pour mettre en forme un <xref:System.DateTime> avec des fractions de seconde mais sans informations de décalage.

2. « Date et heure »
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'ssZ'

        Utilisé pour mettre en forme un <xref:System.DateTime> sans fractions de seconde, mais avec un décalage UTC.

    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFFZ"

        Utilisé pour mettre en forme un <xref:System.DateTime> avec des fractions de seconde et avec un décalage UTC.

    3. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS (' + '/'-') HH' : 'mm'

        Utilisé pour mettre en forme un <xref:System.DateTime> ou <xref:System.DateTimeOffset> sans fractions de seconde, mais avec un décalage local.

    4. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF (' + '/'-') HH' : 'mm'

        Utilisé pour mettre en forme un <xref:System.DateTime> ou <xref:System.DateTimeOffset> avec des fractions de seconde et avec un décalage local.

Si la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) d’une instance de <xref:System.DateTime> ou <xref:System.DateTimeOffset> a des zéros de fin dans ses fractions de seconde, <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter> mettre en forme une représentation de l’instance sans zéros de fin.
Par exemple, une instance de <xref:System.DateTime> dont la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) est `2019-04-24T14:50:17.1010000Z`, sera mise en forme comme `2019-04-24T14:50:17.101Z` par <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter>.

Si la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) d’une instance de <xref:System.DateTime> ou <xref:System.DateTimeOffset> a des zéros dans ses fractions de seconde, <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter> mettre en forme une représentation de l’instance sans fractions de seconde.
Par exemple, une instance de <xref:System.DateTime> dont la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) est `2019-04-24T14:50:17.0000000+02:00`, sera mise en forme comme `2019-04-24T14:50:17+02:00` par <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter>.

La troncation des zéros dans les chiffres de fractions de seconde permet d’écrire la plus petite sortie nécessaire pour conserver les informations sur un aller-retour.

Un maximum de 7 chiffres de fractions de seconde sont écrits. Cela s’aligne avec l’implémentation de <xref:System.DateTime>, qui est limitée à cette résolution.
