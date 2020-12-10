---
title: Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json
description: Découvrez comment activer la correspondance des noms de propriété ne respectant pas la casse lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3e2fb8cbdd35e772b5e97c731199f69aa834bd0a
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009740"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a>Comment activer la correspondance des noms de propriétés ne respectant pas la casse avec System.Text.Json

Dans cet article, vous allez apprendre à activer la correspondance des noms de propriété qui ne respectent pas la casse avec l' `System.Text.Json` espace de noms.

## <a name="case-insensitive-property-matching"></a>Correspondance de propriété ne respectant pas la casse

Par défaut, la désérialisation recherche les correspondances de noms de propriétés respectant la casse entre JSON et les propriétés de l’objet cible. Pour modifier ce comportement, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true` :

> [!NOTE]
> La [valeur par défaut du Web](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) ne respecte pas la casse.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

Voici un exemple de JSON avec les noms de propriété de casse mixte. Il peut être désérialisé dans le type suivant qui a des noms de propriété de casse Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour sérialiser et désérialiser JSON](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Préserver les références](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
