---
title: Comment instancier JsonSerializerOptions avec System.Text.Json
description: Apprenez à éviter les problèmes de performances et à utiliser les constructeurs disponibles pour les instances JsonSerializerOptions.
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 257c99e117dea9a9b3ab2352c9a442d71a2cdabd
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918552"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>Comment instancier des instances JsonSerializerOptions avec System.Text.Json

Cet article explique comment éviter les problèmes de performances lorsque vous utilisez <xref:System.Text.Json.JsonSerializerOptions> . Il montre également comment utiliser les constructeurs paramétrables qui sont disponibles.

## <a name="reuse-jsonserializeroptions-instances"></a>Réutiliser les instances JsonSerializerOptions

Si vous utilisez `JsonSerializerOptions` à plusieurs reprises avec les mêmes options, ne créez pas une nouvelle `JsonSerializerOptions` instance à chaque fois que vous l’utilisez. Réutilisez la même instance pour chaque appel. Ce guide s’applique au code que vous écrivez pour les convertisseurs personnalisés et lorsque vous appelez <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .

Le code suivant illustre la baisse des performances pour l’utilisation de nouvelles instances d’options.

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

Le code précédent sérialise un petit objet 100 000 fois à l’aide de la même instance d’options. Ensuite, il sérialise le même objet le même nombre de fois et crée à chaque fois une nouvelle instance d’options. Une différence de temps d’exécution classique est de 190 par rapport à 40 140 millisecondes. La différence est encore plus importante si vous augmentez le nombre d’itérations.

Le sérialiseur subit une phase de préchauffage pendant la première sérialisation de chaque type dans le graphique d’objets quand une nouvelle instance d’options lui est passée. Cela implique la création d’un cache de métadonnées qui est nécessaire pour la sérialisation. Les métadonnées incluent des délégués aux accesseurs get de propriété, aux Setters, aux arguments de constructeur, aux attributs spécifiés, etc. Ce cache de métadonnées est stocké dans l’instance options. Le même processus de préchauffage et le même cache s’appliquent à la désérialisation.

La taille du cache de métadonnées dans une `JsonSerializerOptions` instance dépend du nombre de types à sérialiser. Si vous passez de nombreux types (par exemple, des types générés dynamiquement) au sérialiseur, la taille du cache continue de croître et peut finir par provoquer un `OutOfMemoryException` .

## <a name="copy-jsonserializeroptions"></a>Copier JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Il existe un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) qui vous permet de créer une nouvelle instance avec les mêmes options qu’une instance existante, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Un `JsonSerializerOptions` constructeur qui prend une instance existante n’est pas disponible dans .net Core 3,1.
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>Valeurs par défaut Web pour JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Voici les options qui ont des valeurs par défaut différentes pour les applications Web :

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

Il y a un [constructeur JsonSerializerOptions] (XREF : System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults) ? View = net-5,0&Preserve-View = true) qui vous permet de créer une nouvelle instance avec les options par défaut que ASP.NET Core utilise pour Web Apps, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Voici les options qui ont des valeurs par défaut différentes pour les applications Web :

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

Un `JsonSerializerOptions` constructeur qui spécifie un jeu de valeurs par défaut n’est pas disponible dans .net Core 3,1.
::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Conserver les références circulaires](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
