---
title: Prise en charge de DateTime et DateTimeOffset dans System.Text.Json
description: Vue d’ensemble de la façon dont les types DateTime et DateTimeOffset sont pris en charge dans la System.Text.Jssur la bibliothèque.
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
ms.openlocfilehash: 020e6903069da2c5d8761c86e890c4e9575a3fae
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188755"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Prise en charge de DateTime et DateTimeOffset dans System.Text.Json

La System.Text.Jssur la bibliothèque analyse et écrit <xref:System.DateTime> les <xref:System.DateTimeOffset> valeurs et en fonction du profil étendu ISO 8601 :-2019.
Les [convertisseurs](xref:System.Text.Json.Serialization.JsonConverter%601) fournissent une prise en charge personnalisée pour la sérialisation et la désérialisation avec <xref:System.Text.Json.JsonSerializer> .
La prise en charge personnalisée peut également être implémentée lors de l’utilisation <xref:System.Text.Json.Utf8JsonReader> de et <xref:System.Text.Json.Utf8JsonWriter> .

## <a name="support-for-the-iso-8601-12019-format"></a>Prise en charge du format ISO 8601-1:2019

Les <xref:System.Text.Json.JsonSerializer> types,, <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> et <xref:System.Text.Json.JsonElement> analysent et écrivent des <xref:System.DateTime> <xref:System.DateTimeOffset> représentations textuelles selon le profil étendu du format ISO 8601-1:2019, par exemple, 2019-07-26T16:59:57-05:00.

<xref:System.DateTime> les <xref:System.DateTimeOffset> données et peuvent être sérialisées avec <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Elles peuvent également être désérialisées avec <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Avec les options par défaut, <xref:System.DateTime> les représentations d’entrée et de <xref:System.DateTimeOffset> texte doivent être conformes au profil ISO 8601-1:2019 étendu.
Toute tentative de désérialisation de représentations qui ne sont pas conformes au profil entraîne la <xref:System.Text.Json.JsonSerializer> levée d’un <xref:System.Text.Json.JsonException> :

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

Le <xref:System.Text.Json.JsonDocument> fournit un accès structuré au contenu d’une charge utile JSON, y compris les <xref:System.DateTime> <xref:System.DateTimeOffset> représentations et. L’exemple ci-dessous montre comment, lorsqu’une collection de températures est donnée, la température moyenne sur lundi peut être calculée :

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Toute tentative de calcul de la température moyenne en fonction d’une charge utile avec des représentations non conformes <xref:System.DateTime> entraînera la <xref:System.Text.Json.JsonDocument> levée d’un <xref:System.FormatException> :

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Les écritures et les données de niveau inférieur <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> <xref:System.DateTimeOffset> :

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> analyse <xref:System.DateTime> et <xref:System.DateTimeOffset> données :

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Si vous tentez de lire des formats non conformes avec <xref:System.Text.Json.Utf8JsonReader> , cela entraînera la levée d’un <xref:System.FormatException> :

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Prise en charge personnalisée pour <xref:System.DateTime> et <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Quand vous utilisez <xref:System.Text.Json.JsonSerializer>

Si vous souhaitez que le sérialiseur effectue une analyse personnalisée ou une mise en forme, vous pouvez implémenter des [convertisseurs personnalisés](xref:System.Text.Json.Serialization.JsonConverter%601).
Voici quelques exemples :

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Utilisation `DateTime(Offset).Parse` de et `DateTime(Offset).ToString`

Si vous ne pouvez pas déterminer les formats de vos représentations d’entrée <xref:System.DateTime> ou de <xref:System.DateTimeOffset> texte, vous pouvez utiliser la `DateTime(Offset).Parse` méthode dans la logique de lecture de votre convertisseur. Cela vous permet d’utiliser. Prise en charge étendue nette pour l’analyse de divers <xref:System.DateTime> <xref:System.DateTimeOffset> formats de texte, y compris les chaînes non ISO 8601 et les formats ISO 8601 qui ne sont pas conformes au profil ISO 8601-1:2019 étendu. Cette approche est beaucoup moins performante que l’utilisation de l’implémentation native du sérialiseur.

Pour la sérialisation, vous pouvez utiliser la `DateTime(Offset).ToString` méthode dans votre logique d’écriture de convertisseur. Cela vous permet d’écrire <xref:System.DateTime> des <xref:System.DateTimeOffset> valeurs et à l’aide de l’un des [formats de date et d’heure standard](../base-types/standard-date-and-time-format-strings.md), ainsi que des [formats de date et d’heure personnalisés](../base-types/custom-date-and-time-format-strings.md).
Cela est également beaucoup moins performant que l’utilisation de l’implémentation native du sérialiseur.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Lors de <xref:System.Text.Json.Serialization.JsonConverter%601> l’implémentation de, et `T` est <xref:System.DateTime> , le `typeToConvert` paramètre sera toujours `typeof(DateTime)` .
Le paramètre est utile pour gérer les cas polymorphes et lors de l’utilisation de génériques pour obtenir `typeof(T)` de façon performante.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Utilisation <xref:System.Buffers.Text.Utf8Parser> de et <xref:System.Buffers.Text.Utf8Formatter>

Vous pouvez utiliser les méthodes d’analyse et de mise en forme rapides UTF-8 dans votre logique de conversion si vos représentations d’entrée <xref:System.DateTime> ou de <xref:System.DateTimeOffset> texte sont conformes à l’une des [chaînes de format de date et d’heure standard](../base-types/standard-date-and-time-format-strings.md)"R", "l", "O" ou "G", ou si vous souhaitez écrire en fonction de l’un de ces formats. C’est beaucoup plus rapide que d’utiliser `DateTime(Offset).Parse` et `DateTime(Offset).ToString` .

Cet exemple montre un convertisseur personnalisé qui sérialise et désérialise des <xref:System.DateTime> valeurs selon [le format standard « R »](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Le format standard « R » aura toujours une longueur de 29 caractères.
>
> Le format « l » (minuscule « L ») n’est pas documenté avec les autres [chaînes de format de date et d’heure standard](../base-types/standard-date-and-time-format-strings.md) , car il est pris en charge uniquement par les `Utf8Parser` `Utf8Formatter` types et. Le format est RFC 1123 en minuscules (une version en minuscules du format « R »), par exemple : « Thou, 25 Jul 2019 06:36:07 GMT ».

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Utilisation de `DateTime(Offset).Parse` comme secours pour l’analyse native du sérialiseur

Si vous vous attendez généralement à ce que votre entrée <xref:System.DateTime> ou vos <xref:System.DateTimeOffset> données soient conformes au profil ISO 8601-1:2019 étendu, vous pouvez utiliser la logique d’analyse native du sérialiseur. Vous pouvez également implémenter un mécanisme de secours uniquement dans le cas.
Cet exemple montre que, après l’échec de l’analyse d’une <xref:System.DateTime> représentation textuelle à l’aide de <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> , le convertisseur analyse les données avec succès à l’aide de <xref:System.DateTime.Parse(System.String)> .

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Lors de l’écriture avec <xref:System.Text.Json.Utf8JsonWriter>

Si vous souhaitez écrire une représentation personnalisée <xref:System.DateTime> ou <xref:System.DateTimeOffset> textuelle avec <xref:System.Text.Json.Utf8JsonWriter> , vous pouvez mettre en forme votre représentation personnalisée en <xref:System.String> , `ReadOnlySpan<Byte>` , `ReadOnlySpan<Char>` ou <xref:System.Text.Json.JsonEncodedText> , puis la passer à la <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> méthode ou correspondante <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> .

L’exemple suivant montre comment créer un <xref:System.DateTime> format personnalisé avec <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> , puis écrit avec la <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> méthode :

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Lors de la lecture avec <xref:System.Text.Json.Utf8JsonReader>

Si vous souhaitez lire une représentation personnalisée <xref:System.DateTime> ou <xref:System.DateTimeOffset> textuelle avec <xref:System.Text.Json.Utf8JsonReader> , vous pouvez obtenir la valeur du jeton JSON actuel en <xref:System.String> utilisant <xref:System.Text.Json.Utf8JsonReader.GetString> , puis analyser la valeur à l’aide d’une logique personnalisée.

L’exemple suivant montre comment une <xref:System.DateTimeOffset> représentation textuelle personnalisée peut être récupérée à l’aide de <xref:System.Text.Json.Utf8JsonReader.GetString> , puis analysée à l’aide de <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> :

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Le profil ISO 8601-1:2019 étendu dans System.Text.Jssur

### <a name="date-and-time-components"></a>Composants de date et d’heure

Le profil ISO 8601-1:2019 étendu implémenté dans <xref:System.Text.Json> définit les composants suivants pour les représentations de date et d’heure. Ces composants sont utilisés pour définir différents niveaux de granularité pris en charge lors de l’analyse et de la mise en forme <xref:System.DateTime> et des <xref:System.DateTimeOffset> représentations.

| Composant       | Format                      | Description                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| Month (Mois)           | "MM"                        | 01-12                                                                           |
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

    Ce niveau de granularité est conforme à la norme [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6), un profil largement adopté de la norme ISO 8601, utilisé pour l’échange d’informations de date et d’heure. Toutefois, il existe quelques restrictions dans le System.Text.Jslors de l’implémentation.

    - La RFC 3339 ne spécifie pas un nombre maximal de chiffres de fractions de seconde, mais spécifie qu’au moins un chiffre doit suivre le point, si une section de fractions de seconde est présente. L’implémentation dans System.Text.Jssur autorise jusqu’à 16 chiffres (pour prendre en charge l’interopérabilité avec d’autres langages et infrastructures de programmation), mais analyse uniquement les sept premières. Une <xref:System.Text.Json.JsonException> exception est levée s’il y a plus de 16 chiffres de fractions de seconde lors de la lecture `DateTime` des `DateTimeOffset` instances et.
    - La RFC 3339 autorise les caractères « t » et « z » respectivement à « t » ou « z », mais permet aux applications de limiter la prise en charge uniquement aux variantes majuscules. L’implémentation dans System.Text.Jssur exige qu’elles soient « T » et « Z ». Une <xref:System.Text.Json.JsonException> est levée si les charges utiles d’entrée contiennent « t » ou « z » lors `DateTime` de la lecture et des `DateTimeOffset` instances.
    - RFC 3339 spécifie que les sections de date et d’heure sont séparées par « T », mais permet aux applications de les séparer par un espace («») à la place. System.Text.Jssur requiert que les sections date et heure soient séparées par « T ». Une <xref:System.Text.Json.JsonException> est levée si les charges utiles d’entrée contiennent un espace ("") lors de la lecture `DateTime` et des `DateTimeOffset` instances.

S’il existe des fractions décimales pour les secondes, il doit y avoir au moins un chiffre ; `2019-07-26T00:00:00.` n’est pas autorisé.
Alors que jusqu’à 16 chiffres fractionnaires sont autorisés, seuls les sept premiers sont analysés. Tout au-delà de ce qui est considéré comme un zéro.
Par exemple, `2019-07-26T00:00:00.1234567890` sera analysé comme s’il s’agissait de `2019-07-26T00:00:00.1234567` .
Cela permet de rester compatible avec l' <xref:System.DateTime> implémentation, qui est limitée à cette résolution.

Les secondes bissextiles ne sont pas prises en charge.

### <a name="support-for-formatting"></a>Prise en charge de la mise en forme

Les niveaux de granularité suivants sont définis pour la mise en forme :

1. "'Date complète’t' 'temps partiel'"
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS' ([spécificateur de format pouvant être trié ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Utilisé pour mettre en forme une valeur <xref:System.DateTime> sans fractions de seconde et sans informations de décalage.

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

    Ce niveau de granularité est conforme à la norme [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6).

Si la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) d' <xref:System.DateTime> une <xref:System.DateTimeOffset> instance ou a des zéros de fin dans ses fractions de seconde, <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter> mettra en forme une représentation de l’instance sans zéros de fin.
Par exemple, une <xref:System.DateTime> instance dont la représentation [de format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) est `2019-04-24T14:50:17.1010000Z` , sera mise en forme en tant que `2019-04-24T14:50:17.101Z` par <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter> .

Si la représentation du [format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) d’une <xref:System.DateTime> instance ou contient uniquement des <xref:System.DateTimeOffset> zéros dans ses fractions de seconde, <xref:System.Text.Json.JsonSerializer> et met en <xref:System.Text.Json.Utf8JsonWriter> forme une représentation de l’instance sans les fractions de seconde.
Par exemple, une <xref:System.DateTime> instance dont la représentation [de format aller-retour](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) est `2019-04-24T14:50:17.0000000+02:00` , sera mise en forme en tant que `2019-04-24T14:50:17+02:00` par <xref:System.Text.Json.JsonSerializer> et <xref:System.Text.Json.Utf8JsonWriter> .

La troncation des zéros dans les chiffres de fractions de seconde permet d’écrire la plus petite sortie nécessaire pour conserver les informations sur un aller-retour.

Un maximum de 7 chiffres de fractions de seconde sont écrits. Cela s’aligne avec l' <xref:System.DateTime> implémentation, qui est limitée à cette résolution.
