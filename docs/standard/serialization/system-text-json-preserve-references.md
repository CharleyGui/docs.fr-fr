---
title: Comment conserver des références avec System.Text.Json
description: Apprenez à préserver les références et à gérer les références circulaires lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008732"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a>Comment conserver des références et gérer des références circulaires avec System.Text.Json

::: zone pivot="dotnet-5-0"

Pour conserver les références et gérer les références circulaires, affectez à la valeur <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . Ce paramètre entraîne le comportement suivant :

* Lors de la sérialisation :

  Lors de l’écriture de types complexes, le sérialiseur écrit également des propriétés de métadonnées ( `$id` , `$values` et `$ref` ).

* Lors de la désérialisation :

  Les métadonnées sont attendues (même si elles ne sont pas obligatoires) et le désérialiseur essaie de le comprendre.

Le code suivant illustre l’utilisation du `Preserve` paramètre.

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

Cette fonctionnalité ne peut pas être utilisée pour conserver des types valeur ou des types immuables. Lors de la désérialisation, l’instance d’un type immuable est créée après la lecture de la charge utile entière. Il serait donc impossible de désérialiser la même instance si une référence à celle-ci apparaît dans la charge utile JSON.

Pour les types valeur, les types immuables et les tableaux, aucune métadonnée de référence n’est sérialisée. Lors de la désérialisation, une exception est levée si `$ref` ou `$id` est trouvé. Toutefois, les types valeur ignorent `$id` (et, `$values` dans le cas des collections) qu’il est possible de désérialiser les charges utiles qui ont été sérialisées à l’aide de Newtonsoft.Json .  Newtonsoft.Json sérialise les métadonnées de ces types.

Pour déterminer si les objets sont égaux, System.Text.Json utilise <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , qui utilise l’égalité <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> de référence () au lieu de l’égalité des valeurs (lors de la comparaison de <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> deux instances d’objet.

Pour plus d’informations sur la façon dont les références sont sérialisées et désérialisées, consultez <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .

La <xref:System.Text.Json.Serialization.ReferenceResolver> classe définit le comportement de préservation des références sur la sérialisation et la désérialisation. Créez une classe dérivée pour spécifier un comportement personnalisé. Pour obtenir un exemple, consultez [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json dans .NET Core 3,1 prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.
::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Guide pratique pour sérialiser et désérialiser JSON](system-text-json-how-to.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
