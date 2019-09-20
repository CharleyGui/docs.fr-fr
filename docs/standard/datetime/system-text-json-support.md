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
ms.openlocfilehash: 83b1b3a7db63154dccc07325b1a1948a2db3953a
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151827"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Prise en charge de DateTime et DateTimeOffset dans System.Text.Json

La bibliothèque System. Text. JSON analyse et écrit <xref:System.DateTime> les valeurs et <xref:System.DateTimeOffset> en fonction du profil étendu ISO 8601 :-2019.
Les [convertisseurs](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) fournissent une prise en charge personnalisée pour la sérialisation et <xref:System.Text.Json.JsonSerializer>la désérialisation avec.
La prise en charge personnalisée peut également être <xref:System.Text.Json.Utf8JsonReader> implémentée lors de l’utilisation de et. <xref:System.Text.Json.Utf8JsonWriter>

## <a name="support-for-the-iso-8601-12019-format"></a>Prise en charge du format ISO 8601-1:2019

Les <xref:System.Text.Json.JsonSerializer>types <xref:System.Text.Json.Utf8JsonReader> <xref:System.DateTime> ,, et <xref:System.Text.Json.JsonElement> analysent et écrivent<xref:System.DateTimeOffset> des représentations textuelles en fonction du profil étendu du format ISO 8601-1:2019, par exemple, 2019-07-26T16 <xref:System.Text.Json.Utf8JsonWriter> : 59:57-05:00.

<xref:System.DateTime>les <xref:System.DateTimeOffset> données et peuvent être sérialisées <xref:System.Text.Json.JsonSerializer>avec :

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Elles peuvent également être désérialisées avec <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Avec les options par défaut <xref:System.DateTime> , <xref:System.DateTimeOffset> les représentations d’entrée et de texte doivent être conformes au profil ISO 8601-1:2019 étendu.
Toute tentative de désérialisation de représentations qui ne sont pas conformes au profil <xref:System.Text.Json.JsonSerializer> entraîne la levée <xref:System.Text.Json.JsonException>d’un :

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

Le <xref:System.Text.Json.JsonDocument> fournit un accès structuré au contenu d’une charge utile JSON, <xref:System.DateTime> y <xref:System.DateTimeOffset> compris les représentations et. L’exemple ci-dessous montre comment, lorsqu’une collection de températures est donnée, la température moyenne sur lundi peut être calculée :

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Toute tentative de calcul de la température moyenne en fonction d’une charge utile avec <xref:System.DateTime> des représentations non <xref:System.Text.Json.JsonDocument> conformes entraînera <xref:System.FormatException>la levée d’un :

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Les écritures <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> et lesdonnéesdeniveauinférieur:<xref:System.DateTimeOffset>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> analyse et<xref:System.DateTimeOffset> données :

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Si vous tentez de lire des formats non <xref:System.Text.Json.Utf8JsonReader> conformes avec, cela entraînera <xref:System.FormatException>la levée d’un :

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Prise en charge <xref:System.DateTime> personnalisée pour et<xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Quand vous utilisez<xref:System.Text.Json.JsonSerializer>

Si vous souhaitez que le sérialiseur effectue une analyse personnalisée ou une mise en forme, vous pouvez implémenter des [convertisseurs personnalisés](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).
Voici quelques exemples :

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Utilisation `DateTime(Offset).Parse` de et`DateTime(Offset).ToString`

Si vous ne pouvez pas déterminer les formats de <xref:System.DateTime> vos <xref:System.DateTimeOffset> représentations d’entrée ou de texte, `DateTime(Offset).Parse` vous pouvez utiliser la méthode dans la logique de lecture de votre convertisseur. Cela vous permet d’utiliser. Prise en charge étendue nette pour l’analyse <xref:System.DateTime> de <xref:System.DateTimeOffset> divers formats de texte, y compris les chaînes non ISO 8601 et les formats ISO 8601 qui ne sont pas conformes au profil ISO 8601-1:2019 étendu. Cette approche est beaucoup moins performante que l’utilisation de l’implémentation native du sérialiseur.

Pour la sérialisation, vous pouvez utiliser la `DateTime(Offset).ToString` méthode dans votre logique d’écriture de convertisseur. Cela vous permet d’écrire <xref:System.DateTime> des <xref:System.DateTimeOffset> valeurs et à l’aide de l’un des [formats de date et d’heure standard](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), ainsi que des [formats de date et d’heure personnalisés](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
Cela est également beaucoup moins performant que l’utilisation de l’implémentation native du sérialiseur.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Lors de <xref:System.Text.Json.Serialization.JsonConverter%601>l’implémentation `T` de <xref:System.DateTime>, et `typeToConvert` est, le paramètre `typeof(DateTime)`sera toujours.
Le paramètre est utile pour gérer les cas polymorphes et lors de l’utilisation de `typeof(T)` génériques pour obtenir de façon performante.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Utilisation <xref:System.Buffers.Text.Utf8Parser> de et<xref:System.Buffers.Text.Utf8Formatter>

Vous pouvez utiliser les méthodes d’analyse et de mise en forme rapides UTF-8 dans votre logique de convertisseur si <xref:System.DateTime> vos <xref:System.DateTimeOffset> représentations d’entrée ou de texte sont conformes à l’une des [chaînes de format de date et d’heure standard](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" ou "G", ou que vous souhaitez écrivez en fonction de l’un de ces formats. C’est beaucoup plus rapide que `DateTime(Offset).Parse` d' `DateTime(Offset).ToString`utiliser et.

Cet exemple montre un convertisseur personnalisé qui sérialise et désérialise <xref:System.DateTime> des valeurs selon [le format standard « R »](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Le format standard « R » aura toujours une longueur de 29 caractères.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Utilisation `DateTime(Offset).Parse` de comme secours pour l’analyse native du sérialiseur

Si vous vous attendez généralement à <xref:System.DateTime> ce <xref:System.DateTimeOffset> que votre entrée ou vos données soient conformes au profil ISO 8601-1:2019 étendu, vous pouvez utiliser la logique d’analyse native du sérialiseur. Vous pouvez également implémenter un mécanisme de secours uniquement dans le cas.
Cet exemple montre que, après l’échec de l' <xref:System.DateTime> analyse d’une <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>représentation textuelle à l’aide de, le convertisseur <xref:System.DateTime.Parse(System.String)>analyse les données avec succès à l’aide de.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Lors de l’écriture avec<xref:System.Text.Json.Utf8JsonWriter>

Si vous souhaitez écrire une représentation personnalisée <xref:System.DateTime> ou <xref:System.DateTimeOffset> textuelle avec <xref:System.Text.Json.Utf8JsonWriter>, <xref:System.String>vous pouvez mettre en forme votre représentation personnalisée en, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`ou <xref:System.Text.Json.JsonEncodedText>, puis la passer au Méthode [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) ou [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) .

L’exemple suivant montre comment créer un <xref:System.DateTime> format personnalisé avec <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, puis écrit avec la <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> méthode :

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Lors de la lecture avec<xref:System.Text.Json.Utf8JsonReader>

Si vous souhaitez lire une représentation personnalisée <xref:System.DateTime> ou <xref:System.DateTimeOffset> textuelle avec <xref:System.Text.Json.Utf8JsonReader>, vous pouvez obtenir la <xref:System.String> valeur du jeton JSON actuel en utilisant <xref:System.Text.Json.Utf8JsonReader.GetString>, puis analyser la valeur à l’aide d’une logique personnalisée.

L’exemple suivant montre comment une représentation <xref:System.DateTimeOffset> textuelle personnalisée peut être récupérée à <xref:System.Text.Json.Utf8JsonReader.GetString>l’aide de, puis <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>analysée à l’aide de :

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Le profil ISO 8601-1:2019 étendu dans System. Text. JSON

### <a name="date-and-time-components"></a>Composants de date et d’heure

Le profil ISO 8601-1:2019 étendu implémenté dans <xref:System.Text.Json> définit les composants suivants pour les représentations de date et d’heure. Ces composants sont utilisés pour définir différents niveaux de granularité pris en charge lors de l’analyse <xref:System.DateTime> et <xref:System.DateTimeOffset> de la mise en forme et des représentations.

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
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS' ([spécificateur de format pouvant être trié ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))
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
Par exemple, `2019-07-26T00:00:00.1234567890` sera analysé comme s' `2019-07-26T00:00:00.1234567`il s’agissait de.
Cela permet de rester compatible avec l' <xref:System.DateTime> implémentation, qui est limitée à cette résolution.

Les secondes bissextiles ne sont pas prises en charge.

### <a name="support-for-formatting"></a>Prise en charge de la mise en forme

Les niveaux de granularité suivants sont définis pour la mise en forme :

1. "'Date complète’t' 'temps partiel'"
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS' ([spécificateur de format pouvant être trié ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        Utilisé pour mettre en <xref:System.DateTime> forme une valeur sans fractions de seconde et sans informations de décalage.

    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF

        Utilisé pour mettre en <xref:System.DateTime> forme un avec des fractions de seconde mais sans informations de décalage.

2. « Date et heure »
    1. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'ssZ'

        Utilisé pour mettre en <xref:System.DateTime> forme <xref:System.DateTimeOffset> un ou sans fractions de seconde, mais avec un décalage UTC.

    2. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFFZ"

        Utilisé pour mettre en <xref:System.DateTime> forme <xref:System.DateTimeOffset> un ou avec des fractions de seconde et avec un décalage UTC.

    3. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS (' + '/'-') HH' : 'mm'

        Utilisé pour mettre en <xref:System.DateTime> forme <xref:System.DateTimeOffset> un ou sans fractions de seconde, mais avec un décalage local.

    4. "chaîne-personnalisée" YYYY'-'MM'-'DD’T’HH-Yyyy'-'mm'-'dd’t’hh' : 'mm' : 'SS'. ' FFFFFFF (' + '/'-') HH' : 'mm'

        Utilisé pour mettre en <xref:System.DateTime> forme <xref:System.DateTimeOffset> un ou avec des fractions de seconde et avec un décalage local.

S’il est présent, un maximum de 7 chiffres fractionnaires sont écrits. Cela s’aligne avec l' <xref:System.DateTime> implémentation, qui est limitée à cette résolution.
