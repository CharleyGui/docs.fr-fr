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
ms.openlocfilehash: 2d663ac8c1c15d61959a62c40d9a3b0993484032
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599074"
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
* [Instancier JsonSerializerOptions](system-text-json-configure-options.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Conserver les références circulaires](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
