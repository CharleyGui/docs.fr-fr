---
title: Comment utiliser des types immuables et des accesseurs non publics avec System.Text.Json
description: Découvrez comment utiliser des types immuables et des accesseurs non publics lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ff8ecec0d70c877b7cbbd0297b85f0d9578ab828
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008823"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a>Comment utiliser des types immuables et des accesseurs non publics avec System.Text.Json

Dans cet article, vous allez apprendre à utiliser des types immuables, tels que des enregistrements, avec l' `System.Text.Json` espace de noms.

## <a name="immutable-types-and-records"></a>Enregistrements et types immuables

::: zone pivot="dotnet-5-0"
`System.Text.Json` peut utiliser un constructeur paramétrable, ce qui rend possible la désérialisation d’une classe ou d’un struct immuable. Pour une classe, si le seul constructeur est un constructeur paramétrable, ce constructeur sera utilisé. Pour un struct ou une classe avec plusieurs constructeurs, spécifiez celui-ci à utiliser en appliquant l’attribut [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) . Lorsque l’attribut n’est pas utilisé, un constructeur sans paramètre public est toujours utilisé, le cas échéant. L’attribut peut uniquement être utilisé avec des constructeurs publics. L’exemple suivant utilise l' `[JsonConstructor]` attribut :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

Les enregistrements en C# 9 sont également pris en charge, comme illustré dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

Pour les types immuables, car tous leurs accesseurs set de propriété sont non publics, consultez la section suivante à propos des [accesseurs de propriété non publics](#non-public-property-accessors).
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` et la prise en charge des enregistrements C# 9 ne sont pas disponibles dans .NET Core 3,1.
::: zone-end

## <a name="non-public-property-accessors"></a>Accesseurs de propriété non publics

::: zone pivot="dotnet-5-0"
Pour activer l’utilisation d’un accesseur de propriété non public, utilisez l’attribut [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) , comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Les accesseurs de propriété non publics ne sont pas pris en charge dans .NET Core 3,1. Pour plus d’informations, consultez [l' Newtonsoft.Json article migrer à partir de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).
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
* [Préserver les références](system-text-json-preserve-references.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
