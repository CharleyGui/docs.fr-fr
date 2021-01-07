---
title: Types de collections pris en charge dans System.Text.Json
description: Découvrez les types de collections pris en charge pour la sérialisation par les API dans l' System.Text.Json espace de noms.
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970992"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a>Types de collections pris en charge dans System.Text.Json

Cet article donne une vue d’ensemble des regroupements pris en charge pour la sérialisation et la désérialisation. <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> prend en charge un type de collection pour la sérialisation s’il :

* Dérive de <xref:System.Collections.IEnumerable>.
* Contient des éléments qui sont sérialisables.

Le sérialiseur appelle la <xref:System.Collections.IEnumerable.GetEnumerator> méthode et écrit les éléments.

La désérialisation est plus compliquée et n’est pas prise en charge pour certains types de collections.

Les sections suivantes sont organisées par espace de noms et indiquent les types pris en charge pour la sérialisation et la désérialisation.

## <a name="systemcollections-namespace"></a>Espace de noms System.Collections

| Type                                      | Sérialisation | Désérialisation |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | ✔️           | ✔️              |
| <xref:System.Collections.BitArray>        | ✔️           | ❌              |
| <xref:System.Collections.DictionaryEntry> | ✔️           | ✔️              |
| <xref:System.Collections.Hashtable>       | ✔️           | ✔️              |
| <xref:System.Collections.Queue>           | ✔️           | ✔️              |
| <xref:System.Collections.SortedList>      | ✔️           | ✔️              |
| <xref:System.Collections.Stack>           | ✔️           | ✔️              |
| <xref:System.Collections.ICollection>     | ✔️           | ✔️              |
| <xref:System.Collections.IDictionary>     | ✔️           | ✔️              |
| <xref:System.Collections.IEnumerable>     | ✔️           | ✔️              |
| <xref:System.Collections.IList>           | ✔️           | ✔️              |

## <a name="systemcollectionsgeneric-namespace"></a>Espace de noms System.Collections.Generic

::: zone pivot="dotnet-5-0"

| Type                                                      | Sérialisation | Désérialisation |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Generic.Dictionary%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedDictionary%602> \* | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedList%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IDictionary%602> \*      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyDictionary%602> \* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Type                                                                                            | Sérialisation | Désérialisation |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [Dictionnaire \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>                                                     | ✔️           | ✔️              |
| [SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*    | ✔️           | ✔️              |
| [SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | ✔️           | ✔️              |
| [IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | ✔️           | ✔️              |
| [IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                                                      | ✔️           | ✔️              |

::: zone-end

\* Consultez [types de clés pris en charge](#supported-key-types).

## <a name="systemcollectionsimmutable-namespace"></a>Espace de noms System. Collections. immuable

::: zone pivot="dotnet-5-0"

| Type                                                              | Sérialisation | Désérialisation |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*  | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableDictionary%602> \*\* | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*        | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Type                                                                                                          | Sérialisation | Désérialisation |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | ✔️           | ✔️              |
| [ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | ✔️           | ✔️              |
| [ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*| ✔️       | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*                                                     | ✔️           | ✔️              |
| [IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*                                                    | ✔️           | ✔️              |

::: zone-end

\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

\*\* Consultez [types de clés pris en charge](#supported-key-types).

## <a name="systemcollectionsspecialized-namespace"></a>Espace de noms System.Collections.Specialized

| Type                                                      | Sérialisation | Désérialisation |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | ✔️           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | ✔️           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.StringCollection>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | ✔️           | ❌              |

\* Lorsque <xref:System.Collections.Specialized.BitVector32> est désérialisé, la <xref:System.Collections.Specialized.BitVector32.Data> propriété est ignorée, car elle n’a pas d’accesseur Set public. Aucune exception n’est générée.

## <a name="systemcollectionsconcurrent-namespace"></a>Espace de noms System.Collections.Concurrent

::: zone pivot="dotnet-5-0"

| Type                                                          | Sérialisation | Désérialisation |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \*   | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Type                                                        | Sérialisation | Désérialisation |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | ✔️           | ❌              |
| [ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\* |✔️|✔️|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \* | ✔️           | ✔️              |

::: zone-end

\*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

\*\* Consultez [types de clés pris en charge](#supported-key-types).

## <a name="systemcollectionsobjectmodel-namespace"></a>Espace de noms System.Collections.ObjectModel

::: zone pivot="dotnet-5-0"

| Type                                                           | Sérialisation | Désérialisation |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | ✔️    | ❌             |

\* Les non- `string` clés ne sont pas prises en charge.

::: zone-end

::: zone pivot="dotnet-core-3-1"

| Type                                                           | Sérialisation | Désérialisation |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| [Objet ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| ✔️     | ❌             |

\* Consultez [types de clés pris en charge](#supported-key-types).

::: zone-end

## <a name="custom-collections"></a>Regroupements personnalisés

Tout type de collection qui n’est pas dans l’un des espaces de noms précédents est considéré comme une collection personnalisée. Ces types incluent des types définis par l’utilisateur et des types définis par ASP.NET Core. Par exemple, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> se trouve dans ce groupe.

Toutes les collections personnalisées (tout ce qui dérive de `IEnumerable` ) sont prises en charge pour la sérialisation, à condition que leurs types d’éléments soient pris en charge.

### <a name="custom-collections-with-deserialization-support"></a>Collections personnalisées avec prise en charge de la désérialisation

Une collection personnalisée est prise en charge pour la désérialisation si :

::: zone pivot="dotnet-5-0"

* N’est pas une interface ni abstraite.
* A un constructeur sans paramètre.
* Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .
* Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <xref:System.Collections.Generic.IDictionary%602> \*\*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

::: zone pivot="dotnet-core-3-1"

* N’est pas une interface ni abstraite.
* A un constructeur sans paramètre.
* Contient les types d’éléments pris en charge par <xref:System.Text.Json.JsonSerializer> .
* Implémente ou hérite d’une ou plusieurs des interfaces ou classes suivantes :
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * [IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

  \*Consultez [prendre en charge l’aller \<T> -retour pour la pile](system-text-json-converters-how-to.md#support-round-trip-for-stackt).

  \*\* Consultez [types de clés pris en charge](#supported-key-types).

### <a name="custom-collections-with-known-issues"></a>Regroupements personnalisés avec problèmes connus

Il existe des problèmes connus avec les regroupements personnalisés suivants :

- <xref:System.Dynamic.ExpandoObject>: Consultez [dotnet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).
- <xref:System.Dynamic.DynamicObject>: Consultez [dotnet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).
- <xref:System.Data.DataTable>: Consultez [dotnet/docs # 21366](https://github.com/dotnet/docs/issues/21366).
- <xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).
- <xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Consultez [dotnet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).

Pour plus d’informations sur les problèmes connus, consultez la rubrique [problèmes ouverts dans System.Text.Json ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).

## <a name="supported-key-types"></a>Types de clé pris en charge

::: zone pivot="dotnet-5-0"

Les types pris en charge pour les clés `Dictionary` et `SortedList` sont les suivants :

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* `Object` (Uniquement lors de la sérialisation et si le type de Runtime est l’un des types pris en charge dans cette liste.)
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

\*\* Les non- `string` clés pour les `Dictionary` types et ne `SortedList` sont pas prises en charge dans .net Core 3,1.

::: zone-end

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Instancier des instances JsonSerializerOptions](system-text-json-configure-options.md)
* [Activer la correspondance non sensible à la casse](system-text-json-character-casing.md)
* [Personnaliser les noms et valeurs de propriété](system-text-json-customize-properties.md)
* [Ignorer les propriétés](system-text-json-ignore-properties.md)
* [Autoriser JSON non valide](system-text-json-invalid-json.md)
* [Gérer le JSON de dépassement](system-text-json-handle-overflow.md)
* [Préserver les références](system-text-json-preserve-references.md)
* [Types immuables et accesseurs non publics](system-text-json-immutability.md)
* [Sérialisation polymorphe](system-text-json-polymorphism.md)
* [Migrer de Newtonsoft.Jsvers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Écrire des sérialiseurs et des désérialiseurs personnalisés](write-custom-serializer-deserializer.md)
* [Écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [Prise en charge DateTime et DateTimeOffset](../datetime/system-text-json-support.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
