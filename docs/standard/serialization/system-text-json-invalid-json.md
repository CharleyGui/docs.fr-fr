---
title: Comment autoriser certains types de JSON non valide avec System.Text.Json
description: Découvrez comment autoriser les commentaires, les virgules de fin et les nombres entre guillemets lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1b6402952c4765290d22b530834ed831a68bd2fe
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851241"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a>Comment autoriser certains types de JSON non valide avec System.Text.Json

Dans cet article, vous allez apprendre comment autoriser des commentaires, des virgules de fin et des nombres entre guillemets dans JSON, et comment écrire des nombres sous forme de chaînes.

## <a name="allow-comments-and-trailing-commas"></a>Autoriser les commentaires et les virgules de fin

Par défaut, les commentaires et les virgules de fin ne sont pas autorisés dans JSON. Pour autoriser les commentaires dans le JSON, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> `JsonCommentHandling.Skip` .
Et pour autoriser les virgules de fin, affectez à la propriété la valeur <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> `true` . L’exemple suivant montre comment autoriser les deux :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

Voici un exemple de code JSON avec des commentaires et une virgule de fin :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a>Autoriser ou écrire des nombres entre guillemets

::: zone pivot="dotnet-5-0"

Certains sérialiseurs encodent les nombres sous forme de chaînes JSON (entourées de guillemets).

Par exemple :

```json
{
    "DegreesCelsius": "23"
}
```

À la place de :

```json
{
    "DegreesCelsius": 23
}
```

Pour sérialiser des nombres entre guillemets ou accepter des nombres dans des guillemets dans le graphique d’objet d’entrée entier, définissez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

Lorsque vous utilisez `System.Text.Json` indirectement par le biais de ASP.net Core, les nombres entre guillemets sont autorisés lors de la désérialisation, car ASP.net Core spécifie les [options par défaut du Web](xref:System.Text.Json.JsonSerializerDefaults.Web).

Pour autoriser ou écrire des nombres entre guillemets pour des propriétés, des champs ou des types spécifiques, utilisez l’attribut [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) .
::: zone-end

::: zone pivot="dotnet-core-3-1"
`System.Text.Json` dans .NET Core 3,1 ne prend pas en charge la sérialisation ou la désérialisation des nombres placés entre guillemets. Pour plus d’informations, consultez [autoriser ou écrire des nombres dans des guillemets](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).
::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Instancier JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Conserver les références circulaires](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
