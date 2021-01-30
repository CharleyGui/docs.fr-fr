---
title: Comment personnaliser l’encodage de caractères avec System.Text.Json
description: Découvrez comment personnaliser l’encodage de caractères lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 136a75ab73767fd79f99caa1d1387706ab655473
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215977"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a>Comment personnaliser l’encodage de caractères avec System.Text.Json

Par défaut, le sérialiseur échappe tous les caractères non-ASCII. Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère. Par exemple, si la `Summary` propriété dans le JSON suivant est définie sur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a>Sérialiser les jeux de caractères de la langue

Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

Ce code n’échappe pas aux caractères cyrilliques ou grecs. Si la `Summary` propriété a la valeur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Par défaut, l’encodeur est initialisé avec la <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> plage.

Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

## <a name="serialize-specific-characters"></a>Sérialiser des caractères spécifiques

Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés. L’exemple suivant sérialise uniquement les deux premiers caractères de `жарко` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

Voici un exemple de JSON généré par le code précédent :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a>Listes de blocage

Les sections précédentes montrent comment spécifier des listes d’autorisation de points de code ou de plages que vous ne souhaitez pas placer dans une séquence d’échappement. Toutefois, il existe des listes de blocage globales et spécifiques à l’encodeur qui peuvent remplacer certains points de code dans votre liste verte. Les points de code d’une liste rouge sont toujours placés dans une séquence d’échappement, même s’ils sont inclus dans votre liste verte.

### <a name="global-block-list"></a>Liste rouge globale

La liste rouge globale contient des éléments tels que les caractères à usage privé, les caractères de contrôle, les points de code non définis et certaines catégories Unicode, telles que la [catégorie Space_Separator](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), à l’exception de `U+0020 SPACE` . Par exemple, `U+3000 IDEOGRAPHIC SPACE` est placé dans une séquence d’échappement même si vous spécifiez la plage Unicode des [symboles CJC et des signes de ponctuation (u +3000-u + 303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) comme liste verte.

La liste rouge globale est un détail d’implémentation qui a changé dans chaque version de .NET Core et dans .NET 5. N’effectuez pas de dépendance sur un caractère qui est membre (ou n’est pas membre de) la liste rouge globale.

### <a name="encoder-specific-block-lists"></a>Listes de blocs spécifiques à l’encodeur

Les exemples de points de code bloqués spécifiques à l’encodeur incluent `'<'` et `'&'` pour l' [encodeur html](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` pour l' [encodeur JSON](xref:System.Text.Encodings.Web.JavaScriptEncoder)et `'%'` pour l' [encodeur d’URL](xref:System.Text.Encodings.Web.UrlEncoder). Par exemple, l’encodeur HTML échappe toujours à l’esperluette ( `'&'` ), même si l’esperluette est `BasicLatin` comprise dans la plage et que tous les encodeurs sont initialisés avec `BasicLatin` par défaut.

## <a name="serialize-all-characters"></a>Sérialiser tous les caractères

Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :
>
> * Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .
> * Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu* de caractères.
>
> Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8. Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` . N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour sérialiser et désérialiser JSON](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Préserver les références](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
