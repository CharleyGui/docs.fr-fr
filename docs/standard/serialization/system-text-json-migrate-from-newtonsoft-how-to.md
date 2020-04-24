---
title: Migrer Newtonsoft.Json de System.Text.Json vers-.net
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0828a5654171df39230055215903d3a49690155d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739241"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Comment migrer de Newtonsoft. JSON vers System. Text. JSON

Cet article explique comment effectuer une migration de [Newtonsoft. JSON](https://www.newtonsoft.com/json) vers <xref:System.Text.Json>.

L' `System.Text.Json` espace de noms fournit des fonctionnalités pour sérialiser vers et désérialiser à partir de JavaScript Object Notation (JSON). La `System.Text.Json` bibliothèque est incluse dans l’infrastructure partagée [.net Core 3,0](https://aka.ms/netcore3download) . Pour les autres frameworks cibles, installez le package NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Le package prend en charge :

* .NET Standard 2,0 et versions ultérieures
* .NET Framework 4.7.2 et versions ultérieures
* .NET Core 2,0, 2,1 et 2,2

`System.Text.Json`se concentre principalement sur les performances, la sécurité et la conformité aux normes. Il présente certaines différences clés dans le comportement par défaut et n’a pas pour but `Newtonsoft.Json`d’avoir une parité des fonctionnalités avec. Pour certains scénarios, `System.Text.Json` ne dispose pas de fonctionnalités intégrées, mais il existe des solutions de contournement recommandées. Pour les autres scénarios, les solutions de contournement ne sont pas pratiques. Si votre application dépend d’une fonctionnalité manquante, envisagez de signaler [un problème](https://github.com/dotnet/runtime/issues/new) pour déterminer si la prise en charge de votre scénario peut être ajoutée.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

La majeure partie de cet article concerne l’utilisation de <xref:System.Text.Json.JsonSerializer> l’API, mais elle fournit également des conseils sur l’utilisation <xref:System.Text.Json.JsonDocument> de (qui représente les types Document Object Model ou DOM <xref:System.Text.Json.Utf8JsonReader>), <xref:System.Text.Json.Utf8JsonWriter> et.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tableau des différences entre Newtonsoft. JSON et System. Text. JSON

Le tableau suivant répertorie `Newtonsoft.Json` les `System.Text.Json` fonctionnalités et les équivalents. Les équivalents sont classés dans les catégories suivantes :

* Pris en charge par les fonctionnalités intégrées. L’obtention d’un `System.Text.Json` comportement similaire de peut nécessiter l’utilisation d’un attribut ou d’une option globale.
* Non pris en charge, une solution de contournement est possible. Les solutions de contournement sont des [convertisseurs personnalisés](system-text-json-converters-how-to.md), qui peuvent ne pas fournir `Newtonsoft.Json` une parité complète avec les fonctionnalités. Pour certains d’entre eux, un exemple de code est fourni comme exemples. Si vous utilisez ces `Newtonsoft.Json` fonctionnalités, la migration nécessitera des modifications de vos modèles d’objet .net ou d’autres modifications de code.
* Non pris en charge, la solution de contournement n’est pas pratique ou possible. Si vous utilisez ces `Newtonsoft.Json` fonctionnalités, la migration n’est pas possible sans modification significative.

| Fonctionnalité Newtonsoft. JSON                               | System. Text. JSON équivalent |
|-------------------------------------------------------|-----------------------------|
| Désérialisation non sensible à la casse par défaut           | ✔️ [paramètre global PropertyNameCaseInsensitive](#case-insensitive-deserialization) |
| Noms des propriétés de casse mixte                             | ✔️ [paramètre global PropertyNamingPolicy](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Échappement de caractères minimal                            | ✔️ [caractère strict de la séquence d’échappement, configurable](#minimal-character-escaping) |
| `NullValueHandling.Ignore`paramètre global             | [option globale ✔️ IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Autoriser les commentaires                                        | ✔️ [paramètre global ReadCommentHandling](#comments) |
| Autoriser les virgules de fin                                 | ✔️ [paramètre global AllowTrailingCommas](#trailing-commas) |
| Inscription de convertisseur personnalisé                         | ✔️ [ordre de priorité différent](#converter-registration-precedence) |
| Aucune profondeur maximale par défaut                           | ✔️ [profondeur maximale par défaut 64, configurable](#maximum-depth) |
| Prise en charge d’un large éventail de types                    | ⚠️[Certains types nécessitent des convertisseurs personnalisés](#types-without-built-in-support) |
| Désérialiser des chaînes sous forme de nombres                        | ⚠️[Non pris en charge, solution de contournement, exemple](#quoted-numbers) |
| Désérialiser `Dictionary` avec une clé qui n’est pas une chaîne          | ⚠️[Non pris en charge, solution de contournement, exemple](#dictionary-with-non-string-key) |
| Sérialisation polymorphe                             | ⚠️[Non pris en charge, solution de contournement, exemple](#polymorphic-serialization) |
| Désérialisation polymorphe                           | ⚠️[Non pris en charge, solution de contournement, exemple](#polymorphic-deserialization) |
| Désérialiser le type inféré en `object` propriétés      | ⚠️[Non pris en charge, solution de contournement, exemple](#deserialization-of-object-properties) |
| Désérialiser le `null` littéral JSON en types valeur non Nullable | ⚠️[Non pris en charge, solution de contournement, exemple](#deserialize-null-to-non-nullable-type) |
| Désérialiser en classes et structs immuables          | ⚠️[Non pris en charge, solution de contournement, exemple](#deserialize-to-immutable-classes-and-structs) |
| Attribut `[JsonConstructor]`                         | ⚠️[Non pris en charge, solution de contournement, exemple](#specify-constructor-to-use) |
| `Required`définir sur `[JsonProperty]` l’attribut        | ⚠️[Non pris en charge, solution de contournement, exemple](#required-properties) |
| `NullValueHandling`définir sur `[JsonProperty]` l’attribut | ⚠️[Non pris en charge, solution de contournement, exemple](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`définir sur `[JsonProperty]` l’attribut | ⚠️[Non pris en charge, solution de contournement, exemple](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`paramètre global                 | ⚠️[Non pris en charge, solution de contournement, exemple](#conditionally-ignore-a-property) |
| `DefaultContractResolver`pour exclure des propriétés       | ⚠️[Non pris en charge, solution de contournement, exemple](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` paramètres   | ⚠️[Non pris en charge, solution de contournement, exemple](#specify-date-format) |
| Rappels                                             | ⚠️[Non pris en charge, solution de contournement, exemple](#callbacks) |
| Prise en charge des champs publics et non publics              | ⚠️[Non pris en charge, solution de contournement](#public-and-non-public-fields) |
| Prise en charge des accesseurs set et des accesseurs get de propriété internes et privées | ⚠️[Non pris en charge, solution de contournement](#internal-and-private-property-setters-and-getters) |
| Méthode `JsonConvert.PopulateObject`                   | ⚠️[Non pris en charge, solution de contournement](#populate-existing-objects) |
| `ObjectCreationHandling`paramètre global               | ⚠️[Non pris en charge, solution de contournement](#reuse-rather-than-replace-properties) |
| Ajouter aux collections sans Setters                    | ⚠️[Non pris en charge, solution de contournement](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`paramètre global           | ❌[Non pris en charge](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`paramètre global                | ❌[Non pris en charge](#preserve-object-references-and-handle-loops) |
| Prise en `System.Runtime.Serialization` charge des attributs | ❌[Non pris en charge](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`paramètre global                | ❌[Non pris en charge](#missingmemberhandling) |
| Autoriser les noms de propriété sans guillemets                   | ❌[Non pris en charge](#json-strings-property-names-and-string-values) |
| Autoriser les guillemets simples autour des valeurs de chaîne              | ❌[Non pris en charge](#json-strings-property-names-and-string-values) |
| Autoriser les valeurs non-chaîne JSON pour les propriétés de chaîne    | ❌[Non pris en charge](#non-string-values-for-string-properties) |

Il ne s’agit pas d’une `Newtonsoft.Json` liste exhaustive des fonctionnalités. La liste comprend un grand nombre des scénarios qui ont été demandés dans les [problèmes GitHub](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) ou les publications [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) . Si vous implémentez une solution de contournement pour l’un des scénarios répertoriés ici qui n’a pas d’exemple de code, et si vous souhaitez partager votre solution, sélectionnez **cette page** dans la section **Commentaires** en bas de cette page. Cela crée un problème dans le référentiel GitHub de cette documentation et le répertorie également dans la section **Commentaires** sur cette page.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Différences dans le comportement de JsonSerializer par défaut par rapport à Newtonsoft. JSON

<xref:System.Text.Json>est strict par défaut et évite toute estimation ou interprétation au nom de l’appelant, en mettant l’accent sur le comportement déterministe. La bibliothèque est intentionnellement conçue de cette façon pour les performances et la sécurité. `Newtonsoft.Json`est flexible par défaut. Cette différence fondamentale en matière de conception repose sur la plupart des différences spécifiques suivantes dans le comportement par défaut.

### <a name="case-insensitive-deserialization"></a>Désérialisation non sensible à la casse

Pendant la désérialisation, `Newtonsoft.Json` ne respecte pas la casse par défaut. La <xref:System.Text.Json> valeur par défaut est sensible à la casse, ce qui offre de meilleures performances, car elle fait une correspondance exacte. Pour plus d’informations sur la façon d’effectuer une correspondance qui ne respecte pas la casse, consultez [correspondance de propriété](system-text-json-how-to.md#case-insensitive-property-matching)ne respectant pas la casse.

Si vous utilisez `System.Text.Json` indirectement à l’aide de ASP.net Core, vous n’avez rien à faire pour avoir un `Newtonsoft.Json`comportement similaire. ASP.NET Core spécifie les paramètres pour les [noms de propriété en casse mixte](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) et la correspondance ne respectant `System.Text.Json`pas la casse lorsqu’il utilise.

### <a name="minimal-character-escaping"></a>Échappement de caractères minimal

Pendant la sérialisation, `Newtonsoft.Json` est relativement permissif en ce qui concerne les caractères sans les placer dans une séquence d’échappement. Autrement dit, il ne les remplace pas `\uxxxx` par `xxxx` où est le point de code du caractère. Lorsqu’il les échappe, il émet un `\` avant le caractère (par exemple, `"` devient `\"`). <xref:System.Text.Json>échappe les caractères par défaut pour fournir des protections en profondeur contre les attaques de script entre sites (XSS) ou de divulgation d’informations, et utilise la séquence de six caractères. `System.Text.Json`échappe par défaut tous les caractères non-ASCII. vous n’avez donc pas besoin de faire quoi que `StringEscapeHandling.EscapeNonAscii` ce `Newtonsoft.Json`soit si vous utilisez dans. `System.Text.Json`échappe également les caractères HTML, par défaut. Pour plus d’informations sur la façon de remplacer `System.Text.Json` le comportement par défaut, consultez [personnaliser l’encodage des caractères](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Commentaires

Pendant la désérialisation, `Newtonsoft.Json` ignore par défaut les commentaires dans le JSON. La <xref:System.Text.Json> valeur par défaut consiste à lever des exceptions pour les commentaires, car la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les inclut pas. Pour plus d’informations sur l’autorisation des commentaires, consultez [autoriser les commentaires et les virgules de fin](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Virgules de fin

Pendant la désérialisation, `Newtonsoft.Json` ignore les virgules de fin par défaut. Elle ignore également plusieurs virgules de fin (par exemple, `[{"Color":"Red"},{"Color":"Green"},,]`). La <xref:System.Text.Json> valeur par défaut consiste à lever des exceptions pour les virgules de fin, car la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les autorise pas. Pour plus d’informations sur la `System.Text.Json` façon de les accepter, consultez [autoriser les commentaires et les virgules de fin](system-text-json-how-to.md#allow-comments-and-trailing-commas). Il n’existe aucun moyen d’autoriser plusieurs virgules de fin.

### <a name="converter-registration-precedence"></a>Priorité d’inscription du convertisseur

La `Newtonsoft.Json` priorité d’inscription pour les convertisseurs personnalisés est la suivante :

* Attribut sur la propriété
* Attribut sur le type
* [Converters](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) , collection

Dans cet ordre, un convertisseur personnalisé dans la `Converters` collection est substitué par un convertisseur qui est inscrit en appliquant un attribut au niveau du type. Ces deux inscriptions sont remplacées par un attribut au niveau de la propriété.

La <xref:System.Text.Json> priorité d’inscription pour les convertisseurs personnalisés est différente :

* Attribut sur la propriété
* <xref:System.Text.Json.JsonSerializerOptions.Converters>collecte
* Attribut sur le type

La différence réside dans le fait qu’un convertisseur personnalisé `Converters` dans la collection remplace un attribut au niveau du type. L’objectif derrière cet ordre de priorité est de faire en sorte que les modifications au moment de l’exécution remplacent les choix au moment de la conception. Il n’existe aucun moyen de modifier la précédence.

Pour plus d’informations sur l’inscription d’un convertisseur personnalisé, consultez [inscrire un convertisseur personnalisé](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Profondeur maximale

`Newtonsoft.Json`n’a pas de limite de profondeur maximale par défaut. Pour <xref:System.Text.Json> une limite par défaut de 64, elle peut être configurée en définissant <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.

### <a name="json-strings-property-names-and-string-values"></a>Chaînes JSON (noms de propriété et valeurs de chaîne)

Pendant la désérialisation, `Newtonsoft.Json` accepte les noms de propriété placés entre guillemets doubles, apostrophes ou sans guillemets. Il accepte les valeurs de chaîne entourées de guillemets doubles ou de guillemets simples. Par exemple, `Newtonsoft.Json` accepte le code JSON suivant :

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`accepte uniquement les noms de propriété et les valeurs de chaîne dans des guillemets doubles, car ce format est requis par la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) et est le seul format considéré comme un JSON valide.

Une valeur placée entre guillemets simples donne un [JsonException](xref:System.Text.Json.JsonException) avec le message suivant :

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Valeurs qui ne sont pas des chaînes pour les propriétés de chaîne

`Newtonsoft.Json`accepte les valeurs qui ne sont pas des chaînes, telles qu’un nombre `true` ou `false`les littéraux et, pour la désérialisation des propriétés de type chaîne. Voici un exemple de JSON qui `Newtonsoft.Json` désérialise avec succès la classe suivante :

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json`ne désérialise pas les valeurs qui ne sont pas des chaînes dans les propriétés de chaîne. Une valeur qui n’est pas une chaîne reçue pour un champ de chaîne génère un [JsonException](xref:System.Text.Json.JsonException) avec le message suivant :

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scénarios utilisant des JsonSerializer qui requièrent des solutions de contournement

Les scénarios suivants ne sont pas pris en charge par les fonctionnalités intégrées, mais les solutions de contournement sont possibles. Les solutions de contournement sont des [convertisseurs personnalisés](system-text-json-converters-how-to.md), qui peuvent ne pas fournir `Newtonsoft.Json` une parité complète avec les fonctionnalités. Pour certains d’entre eux, un exemple de code est fourni comme exemples. Si vous utilisez ces `Newtonsoft.Json` fonctionnalités, la migration nécessitera des modifications de vos modèles d’objet .net ou d’autres modifications de code.

### <a name="types-without-built-in-support"></a>Types sans prise en charge intégrée

<xref:System.Text.Json>ne fournit pas de prise en charge intégrée pour les types suivants :

* <xref:System.Data.DataTable>et types associés
* Types F #, tels que les [unions discriminées](../../fsharp/language-reference/discriminated-unions.md), les [types d’enregistrements](../../fsharp/language-reference/records.md)et les types d' [enregistrements anonymes](../../fsharp/language-reference/anonymous-records.md).
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>et ses types génériques associés

Les convertisseurs personnalisés peuvent être implémentés pour les types qui n’ont pas de prise en charge intégrée.

### <a name="quoted-numbers"></a>Nombres entre guillemets

`Newtonsoft.Json`peut sérialiser ou désérialiser des nombres représentés par des chaînes JSON (entourées de guillemets). Par exemple, il peut accepter : `{"DegreesCelsius":"23"}` au lieu `{"DegreesCelsius":23}`de. Pour activer ce comportement dans <xref:System.Text.Json>, implémentez un convertisseur personnalisé comme dans l’exemple suivant. Le convertisseur gère les propriétés définies `long`comme suit :

* Il les sérialise en tant que chaînes JSON.
* Il accepte les nombres et nombres JSON dans les guillemets lors de la désérialisation.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Inscrivez ce convertisseur personnalisé à [l’aide d’un attribut](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) sur des propriétés individuelles `long` ou en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

### <a name="dictionary-with-non-string-key"></a>Dictionnaire avec clé non-chaîne

`Newtonsoft.Json`prend en charge les `Dictionary<TKey, TValue>`collections de type. La prise en charge intégrée pour les collections de <xref:System.Text.Json> dictionnaires dans `Dictionary<string, TValue>`est limitée à. Autrement dit, la clé doit être une chaîne.

Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Sérialisation polymorphe

`Newtonsoft.Json`effectue automatiquement la sérialisation polymorphe. Pour plus d’informations sur les fonctionnalités de sérialisation polymorphes <xref:System.Text.Json>limitées de, consultez [sérialisation des propriétés de classes dérivées](system-text-json-how-to.md#serialize-properties-of-derived-classes).

La solution de contournement décrite ici permet de définir des propriétés qui peuvent contenir des `object`classes dérivées comme type. Si cela n’est pas possible, une autre option consiste à créer un `Write` convertisseur avec une méthode pour l’ensemble de la hiérarchie des types d’héritage, comme dans l’exemple de la rubrique [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Désérialisation polymorphe

`Newtonsoft.Json`a un `TypeNameHandling` paramètre qui ajoute des métadonnées de nom de type au JSON lors de la sérialisation. Elle utilise les métadonnées lors de la désérialisation pour effectuer une désérialisation polymorphe. <xref:System.Text.Json>peut effectuer une plage limitée de [sérialisation polymorphe](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mais pas de désérialisation polymorphe.

Pour prendre en charge la désérialisation polymorphe, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="deserialization-of-object-properties"></a>Désérialisation des propriétés de l’objet

Lors `Newtonsoft.Json` de la désérialisation <xref:System.Object>vers, il :

* Déduit le type de valeurs primitives dans la charge utile JSON (autre `null`que) et retourne le `string`stocké `double`, `boolean` `long`,, `DateTime` ou en tant qu’objet boxed. *Les valeurs primitives* sont des valeurs JSON uniques, telles qu’un nombre `true`JSON `false`, une `null`chaîne,, ou.
* Retourne `JObject` ou `JArray` pour les valeurs complexes dans la charge utile JSON. Les *valeurs complexes* sont des collections de paires clé-valeur JSON entre accolades (`{}`) ou des listes de valeurs`[]`entre crochets (). Les propriétés et les valeurs entre accolades ou crochets peuvent avoir des propriétés ou des valeurs supplémentaires.
* Retourne une référence Null lorsque la charge utile a `null` le littéral JSON.

<xref:System.Text.Json>stocke un `JsonElement` boxed pour les valeurs primitives et complexes lors de la <xref:System.Object>désérialisation de en, par exemple :

* Propriété `object`.
* Valeur `object` de dictionnaire.
* Valeur `object` de tableau.
* Racine `object`.

Toutefois, `System.Text.Json` traite `null` de la même `Newtonsoft.Json` façon que et retourne une référence Null lorsque la charge `null` utile contient le littéral JSON.

Pour implémenter l’inférence `object` de type pour les propriétés, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="deserialize-null-to-non-nullable-type"></a>Désérialiser la valeur null en type non Nullable

`Newtonsoft.Json`ne lève pas d’exception dans le scénario suivant :

* `NullValueHandling`a la valeur `Ignore`, et
* Pendant la désérialisation, le JSON contient une valeur null pour un type valeur qui n’autorise pas les valeurs NULL.

Dans le même scénario, <xref:System.Text.Json> lève une exception. (Le paramètre de gestion null correspondant <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>est.)

Si vous êtes propriétaire du type de cible, la meilleure solution consiste à rendre la propriété en question Nullable (par exemple `int` , `int?`remplacer par).

Une autre solution consiste à créer un convertisseur pour le type, comme dans l’exemple suivant qui gère les valeurs `DateTimeOffset` null pour les types :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Inscrivez ce convertisseur personnalisé à l' [aide d’un attribut sur la propriété](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) ou en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

**Remarque :** Le convertisseur précédent **gère les valeurs NULL** de `Newtonsoft.Json` la même façon que pour les poco qui spécifient des valeurs par défaut. Par exemple, supposons que le code suivant représente votre objet cible :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Et supposons que le code JSON suivant est désérialisé à l’aide du convertisseur précédent :

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Après la désérialisation, la `Date` propriété a 1/1/0001 (`default(DateTimeOffset)`), autrement dit, la valeur définie dans le constructeur est remplacée. Étant donné les mêmes POCO et JSON `Newtonsoft.Json` , la désérialisation laisse 1/1/2001 dans la `Date` propriété.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Désérialiser en classes et structs immuables

`Newtonsoft.Json`peut désérialiser des classes et des structs immuables, car il peut utiliser des constructeurs qui ont des paramètres. <xref:System.Text.Json>prend en charge uniquement les constructeurs sans paramètre public. En guise de solution de contournement, vous pouvez appeler un constructeur avec des paramètres dans un convertisseur personnalisé.

Voici un struct immuable avec plusieurs paramètres de constructeur :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

Et voici un convertisseur qui sérialise et désérialise ce struct :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Inscrivez ce convertisseur personnalisé en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Pour obtenir un exemple de convertisseur similaire qui gère les propriétés génériques ouvertes, consultez le [convertisseur intégré pour les paires clé-valeur](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Spécifier le constructeur à utiliser

L' `Newtonsoft.Json` `[JsonConstructor]` attribut vous permet de spécifier le constructeur à appeler lors de la désérialisation vers un poco. <xref:System.Text.Json>prend en charge uniquement les constructeurs sans paramètre. En guise de solution de contournement, vous pouvez appeler le constructeur dont vous avez besoin dans un convertisseur personnalisé. Consultez l’exemple pour [désérialiser des classes et des structs immuables](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Propriétés requises

Dans `Newtonsoft.Json`, vous spécifiez qu’une propriété est requise en `Required` définissant `[JsonProperty]` sur l’attribut. `Newtonsoft.Json`lève une exception si aucune valeur n’est reçue dans le JSON pour une propriété marquée comme obligatoire.

<xref:System.Text.Json>ne lève pas d’exception si aucune valeur n’est reçue pour l’une des propriétés du type cible. Par exemple, si vous avez une `WeatherForecast` classe :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Le code JSON suivant est désérialisé sans erreur :

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Pour faire échouer la désérialisation si `Date` aucune propriété n’est dans le JSON, implémentez un convertisseur personnalisé. L’exemple de code de convertisseur suivant lève une exception si `Date` la propriété n’est pas définie une fois que la désérialisation est terminée :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Inscrivez ce convertisseur personnalisé à l' [aide d’un attribut sur la classe POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Si vous suivez ce modèle, ne transmettez pas l’objet d’options lors de l' <xref:System.Text.Json.JsonSerializer.Serialize%2A> appel <xref:System.Text.Json.JsonSerializer.Deserialize%2A>récursif ou. L’objet d’options contient <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> la collection. Si vous le transmettez à `Serialize` ou `Deserialize`, le convertisseur personnalisé s’appelle lui-même, en effectuant une boucle infinie qui provoque une exception de dépassement de capacité de la pile. Si les options par défaut ne sont pas réalisables, créez une nouvelle instance des options avec les paramètres dont vous avez besoin. Cette approche est lente puisque chaque nouvelle instance est mise en cache de façon indépendante.

Le code de convertisseur précédent est un exemple simplifié. Une logique supplémentaire est nécessaire si vous avez besoin de gérer des attributs (tels que [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) ou des options différentes (telles que des encodeurs personnalisés). En outre, l’exemple de code ne gère pas les propriétés pour lesquelles une valeur par défaut est définie dans le constructeur. Cette approche ne fait pas la différence entre les scénarios suivants :

* Une propriété est absente du JSON.
* Une propriété pour un type non Nullable est présente dans le JSON, mais la valeur est la valeur par défaut pour le type, par exemple zéro pour `int`un.
* Une propriété pour un type valeur Nullable est présente dans le JSON, mais la valeur est null.

### <a name="conditionally-ignore-a-property"></a>Ignorer une propriété de façon conditionnelle

`Newtonsoft.Json`offre plusieurs méthodes pour ignorer de manière conditionnelle une propriété lors de la sérialisation ou de la désérialisation :

* `DefaultContractResolver`vous permet de sélectionner les propriétés à inclure ou exclure, en fonction de critères arbitraires.
* Les `NullValueHandling` paramètres `DefaultValueHandling` et sur `JsonSerializerSettings` vous permettent de spécifier que toutes les propriétés de valeur null ou de valeur par défaut doivent être ignorées.
* Les `NullValueHandling` paramètres `DefaultValueHandling` et de l' `[JsonProperty]` attribut vous permettent de spécifier des propriétés individuelles qui doivent être ignorées lorsqu’elles sont définies sur null ou sur la valeur par défaut.

<xref:System.Text.Json>fournit les méthodes suivantes pour omettre des propriétés lors de la sérialisation :

* L’attribut [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) sur une propriété provoque l’omission de la propriété du JSON pendant la sérialisation.
* L’option [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global vous permet d’exclure toutes les propriétés de valeur null.
* L’option [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) global vous permet d’exclure toutes les propriétés en lecture seule.

Ces options **ne** vous permettent pas de :

* Ignore toutes les propriétés qui ont la valeur par défaut pour le type.
* Ignorer les propriétés sélectionnées qui ont la valeur par défaut pour le type.
* Ignorer les propriétés sélectionnées si leur valeur est null.
* Ignorer les propriétés sélectionnées en fonction de critères arbitraires évalués au moment de l’exécution.

Pour cette fonctionnalité, vous pouvez écrire un convertisseur personnalisé. Voici un exemple de modèle POCO et un convertisseur personnalisé qui illustre cette approche :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Le convertisseur fait en `Summary` sorte que la propriété soit omise de la sérialisation si sa valeur est null, une chaîne vide ou « N/A ».

Inscrivez ce convertisseur personnalisé à l' [aide d’un attribut sur la classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Cette approche nécessite une logique supplémentaire dans les cas suivants :

* Le POCO comprend des propriétés complexes.
* Vous devez gérer des attributs tels que `[JsonIgnore]` ou des options telles que des encodeurs personnalisés.

### <a name="specify-date-format"></a>Spécifier le format de la date

`Newtonsoft.Json`offre plusieurs moyens de contrôler la façon dont `DateTime` les `DateTimeOffset` propriétés des types et sont sérialisées et désérialisées :

* Le `DateTimeZoneHandling` paramètre peut être utilisé pour sérialiser toutes `DateTime` les valeurs en tant que dates UTC.
* Le `DateFormatString` paramètre et `DateTime` les convertisseurs peuvent être utilisés pour personnaliser le format des chaînes de date.

Dans <xref:System.Text.Json>, le seul format qui offre une prise en charge intégrée est ISO 8601-1:2019, car il est largement adopté, sans ambiguïté, et effectue des allers-retours avec précision. Pour utiliser n’importe quel autre format, créez un convertisseur personnalisé. Pour plus d’informations, consultez [prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Rappels

`Newtonsoft.Json`vous permet d’exécuter du code personnalisé à plusieurs points dans le processus de sérialisation ou de désérialisation :

* OnDeserializing (au début de la désérialisation d’un objet)
* OnDeserialized (à la fin de la désérialisation d’un objet)
* OnSerializing (au début de la sérialisation d’un objet)
* OnSerialized (à la fin de la sérialisation d’un objet)

Dans <xref:System.Text.Json>, vous pouvez simuler des rappels en écrivant un convertisseur personnalisé. L’exemple suivant montre un convertisseur personnalisé pour un POCO. Le convertisseur comprend du code qui affiche un message à chaque point qui correspond à `Newtonsoft.Json` un rappel.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Inscrivez ce convertisseur personnalisé à l' [aide d’un attribut sur la classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou en [ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Si vous utilisez un convertisseur personnalisé qui suit l’exemple précédent :

* Le `OnDeserializing` code n’a pas accès à la nouvelle instance poco. Pour manipuler la nouvelle instance POCO au début de la désérialisation, placez ce code dans le constructeur POCO.
* Ne transmettez pas l’objet d’options lors d’un `Serialize` appel `Deserialize`récursif ou. L’objet d’options contient `Converters` la collection. Si vous le transmettez à `Serialize` ou `Deserialize`, le convertisseur sera utilisé, en effectuant une boucle infinie qui entraîne une exception de dépassement de capacité de la pile.

### <a name="public-and-non-public-fields"></a>Champs publics et non publics

`Newtonsoft.Json`peut sérialiser et désérialiser des champs ainsi que des propriétés. <xref:System.Text.Json>fonctionne uniquement avec les propriétés publiques. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="internal-and-private-property-setters-and-getters"></a>Accesseurs set et getters de propriétés internes et privées

`Newtonsoft.Json`peut utiliser des accesseurs set et des accesseurs set de propriété `JsonProperty` privés et internes via l’attribut. <xref:System.Text.Json>prend uniquement en charge les accesseurs set publics. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="populate-existing-objects"></a>Remplir les objets existants

La `JsonConvert.PopulateObject` méthode de `Newtonsoft.Json` désérialise un document JSON vers une instance existante d’une classe, au lieu de créer une nouvelle instance. <xref:System.Text.Json>crée toujours une nouvelle instance du type cible à l’aide du constructeur sans paramètre public par défaut. Les convertisseurs personnalisés peuvent être désérialisés en une instance existante.

### <a name="reuse-rather-than-replace-properties"></a>Réutiliser plutôt que remplacer les propriétés

Le `Newtonsoft.Json` `ObjectCreationHandling` paramètre vous permet de spécifier que les objets dans les propriétés doivent être réutilisés au lieu d’être remplacés lors de la désérialisation. <xref:System.Text.Json>remplace toujours les objets dans les propriétés.  Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="add-to-collections-without-setters"></a>Ajouter aux collections sans Setters

Pendant la désérialisation, `Newtonsoft.Json` ajoute des objets à une collection même si la propriété n’a pas d’accesseur Set. <xref:System.Text.Json>ignore les propriétés qui n’ont pas de méthode setter. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Les scénarios que JsonSerializer ne prend pas en charge actuellement

Pour les scénarios suivants, les solutions de contournement ne sont pas pratiques ou possibles. Si vous utilisez ces `Newtonsoft.Json` fonctionnalités, la migration n’est pas possible sans modification significative.

### <a name="preserve-object-references-and-handle-loops"></a>Conserver les références d’objet et gérer les boucles

Par défaut, `Newtonsoft.Json` sérialise par valeur. Par exemple, si un objet contient deux propriétés qui contiennent une référence au même `Person` objet, les valeurs des propriétés de `Person` cet objet sont dupliquées dans le JSON.

`Newtonsoft.Json`a un `PreserveReferencesHandling` paramètre sur `JsonSerializerSettings` qui vous permet de sérialiser par référence :

* Les métadonnées d’identificateur sont ajoutées au JSON créé pour le premier `Person` objet.
* Le JSON créé pour le deuxième `Person` objet contient une référence à cet identificateur à la place des valeurs de propriété.

`Newtonsoft.Json`a également un `ReferenceLoopHandling` paramètre qui vous permet d’ignorer les références circulaires au lieu de lever une exception.

<xref:System.Text.Json>prend uniquement en charge la sérialisation par valeur et lève une exception pour les références circulaires.

### <a name="systemruntimeserialization-attributes"></a>Attributs System. Runtime. Serialization

<xref:System.Text.Json>ne prend pas en charge `System.Runtime.Serialization` les attributs de l' `DataMemberAttribute` espace `IgnoreDataMemberAttribute`de noms, tels que et.

### <a name="octal-numbers"></a>Nombres octaux

`Newtonsoft.Json`traite les nombres avec un zéro non significatif comme des nombres octaux. <xref:System.Text.Json>n’autorise pas les zéros non significatifs, car la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les autorise pas.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json`peut être configuré pour lever des exceptions pendant la désérialisation si le JSON comprend des propriétés qui sont manquantes dans le type cible. <xref:System.Text.Json>ignore les propriétés supplémentaires dans le JSON, sauf lorsque vous utilisez l' [attribut [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Il n’existe aucune solution de contournement pour la fonctionnalité de membre manquant.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`vous permet de déboguer `TraceWriter` à l’aide d’un pour afficher les journaux qui sont générés par la sérialisation ou la désérialisation. <xref:System.Text.Json>n’effectue pas de journalisation.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument et JsonElement comparés à JToken (comme JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>permet d’analyser et de générer un Document Object Model **en lecture seule** (DOM) à partir de charges utiles JSON existantes. Le DOM fournit un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge utile sont accessibles via <xref:System.Text.Json.JsonElement> le type. Le `JsonElement` type fournit des API pour convertir du texte JSON en types .net courants. `JsonDocument`expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.

### <a name="jsondocument-is-idisposable"></a>JsonDocument est IDisposable

`JsonDocument`crée une vue en mémoire des données dans une mémoire tampon regroupée. Par conséquent, `JObject` contrairement `JArray` à `Newtonsoft.Json`ou, `JsonDocument` le type implémente `IDisposable` et doit être utilisé à l’intérieur d’un bloc using.

Retournez uniquement un `JsonDocument` à partir de votre API si vous souhaitez transférer la propriété de la durée de vie et supprimer la responsabilité de l’appelant. Dans la plupart des scénarios, ce n’est pas nécessaire. Si l’appelant doit travailler avec l’ensemble du document JSON, retournez le <xref:System.Text.Json.JsonElement.Clone%2A> du <xref:System.Text.Json.JsonDocument.RootElement%2A>, qui est un <xref:System.Text.Json.JsonElement>. Si l’appelant doit travailler avec un élément particulier dans le document JSON, retournez le <xref:System.Text.Json.JsonElement.Clone%2A> de ce. <xref:System.Text.Json.JsonElement> Si vous retournez directement `RootElement` le ou un sous-élément sans créer de `Clone`, l’appelant ne pourra pas accéder au retourné `JsonElement` après que le `JsonDocument` qui l’a détenu est supprimé.

Voici un exemple qui vous oblige à créer un `Clone`:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Le code précédent attend un `JsonElement` qui contient une `fileName` propriété. Il ouvre le fichier JSON et crée un `JsonDocument`. La méthode suppose que l’appelant souhaite travailler avec l’ensemble du document, de sorte qu’il retourne `Clone` l' `RootElement`du.

Si vous recevez un `JsonElement` et que vous retournez un sous-élément, il n’est pas nécessaire de `Clone` retourner un du sous-élément. L’appelant est chargé de conserver les `JsonDocument` actifs auxquels `JsonElement` appartient le passé. Par exemple :

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument est en lecture seule

Le <xref:System.Text.Json> DOM ne peut pas ajouter, supprimer ou modifier des éléments JSON. Cette méthode est conçue pour les performances et pour réduire les allocations pour l’analyse des tailles de charge utile JSON courantes (c’est-à-dire < 1 Mo). Si votre scénario utilise actuellement un modèle DOM modifiable, l’une des solutions de contournement suivantes peut être possible :

* Pour créer un `JsonDocument` à partir de zéro (autrement dit, sans passer une charge utile JSON existante `Parse` à la méthode), écrivez le texte JSON à `Utf8JsonWriter` l’aide de et analysez la sortie de cette `JsonDocument`pour créer un nouveau.
* Pour modifier un existant `JsonDocument`, utilisez-le pour écrire du texte JSON, apporter des modifications pendant que vous écrivez et analyser la sortie de celle- `JsonDocument`ci pour en créer une nouvelle.
* Pour fusionner des documents JSON existants, équivalents `JContainer.Merge` aux API `Newtonsoft.Json` `JObject.Merge` ou de, consultez [ce problème GitHub](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement est un struct d’Union

`JsonDocument`expose le `RootElement` en tant que propriété de <xref:System.Text.Json.JsonElement>type, qui est une Union, type struct qui englobe tout élément JSON. `Newtonsoft.Json`utilise des types hiérarchiques dédiés`JArray`comme `JToken` `JObject`,,, et ainsi de suite. `JsonElement`est ce que vous pouvez rechercher et énumérer, et vous pouvez utiliser `JsonElement` pour matérialiser des éléments JSON dans des types .net.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Comment rechercher des sous-éléments dans un JsonDocument et JsonElement

Les recherches de jetons JSON utilisant `JObject` ou `JArray` de `Newtonsoft.Json` ont tendance à être relativement rapides parce qu’il s’agit de recherches dans un dictionnaire. Par comparaison, les recherches `JsonElement` sur requièrent une recherche séquentielle des propriétés et sont donc relativement lentes (par exemple `TryGetProperty`, lors de l’utilisation de). <xref:System.Text.Json>est conçu pour réduire le temps d’analyse initial plutôt que le temps de recherche. Par conséquent, utilisez les approches suivantes pour optimiser les performances lors de `JsonDocument` la recherche à l’aide d’un objet :

* Utilisez les énumérateurs intégrés (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> et <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) au lieu d’effectuer votre propre indexation ou boucles.
* N’effectuez pas de recherche séquentielle sur l' `JsonDocument` ensemble de chaque propriété à `RootElement`l’aide de. Au lieu de cela, recherchez des objets JSON imbriqués en fonction de la structure connue des données JSON. Par exemple, si vous `Grade` recherchez une propriété dans `Student` des objets, parcourez les `Student` objets et récupérez la valeur `Grade` de pour chaque, plutôt que de rechercher `JsonElement` dans tous les `Grade` objets à la recherche de propriétés. Si vous procédez ainsi, vous obtiendrez des passes inutiles sur les mêmes données.

Pour obtenir un exemple de code, consultez [utiliser JsonDocument pour accéder aux données](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader comparé à JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>est un lecteur à hautes performances, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lit à partir d’un [octet ReadOnlySpan\<>](xref:System.ReadOnlySpan%601) ou [\<ReadOnlySequence Byte>](xref:System.Buffers.ReadOnlySequence%601). Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.

Les sections suivantes expliquent les modèles de programmation `Utf8JsonReader`recommandés pour l’utilisation de.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader est un struct Ref

Étant donné `Utf8JsonReader` que le type est un *struct de référence*, il présente [certaines limitations](../../csharp/language-reference/builtin-types/struct.md#ref-struct). Par exemple, il ne peut pas être stocké en tant que champ sur une classe ou un struct autre qu’un struct Ref. Pour obtenir des performances élevées, ce type doit être `ref struct` un, car il doit mettre en cache le [>d’octets\< ](xref:System.ReadOnlySpan%601)d’entrée ReadOnlySpan, qui est lui-même un struct Ref. En outre, ce type est mutable puisqu’il contient l’État. Par conséquent, **transmettez-le par référence** plutôt que par valeur. Le fait de le passer par valeur génère une copie de struct et les modifications d’État ne sont pas visibles par l’appelant. Cela diffère de `Newtonsoft.Json` puisque `Newtonsoft.Json` `JsonTextReader` est une classe. Pour plus d’informations sur l’utilisation des structs de référence, consultez [écrire du code C# sécurisé et efficace](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Lire du texte UTF-8

Pour obtenir les meilleures performances possibles lors de l' `Utf8JsonReader`utilisation de, lisez les charges utiles JSON déjà encodées en tant que texte UTF-8 plutôt qu’en tant que chaînes UTF-16. Pour obtenir un exemple de code, consultez [Filtrer les données à l’aide de Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Lire avec un flux ou un PipeReader

Le `Utf8JsonReader` prend en charge la lecture à partir d’un [octet ReadOnlySpan\<](xref:System.ReadOnlySpan%601) encodé UTF-8>ou [\<ReadOnlySequence Byte>](xref:System.Buffers.ReadOnlySequence%601) (qui est le résultat de <xref:System.IO.Pipelines.PipeReader>la lecture à partir d’un).

Pour la lecture synchrone, vous pouvez lire la charge utile JSON jusqu’à la fin du flux dans un tableau d’octets et la passer dans le lecteur. Pour lire à partir d’une chaîne (qui est encodée au format UTF-16 <xref:System.Text.Encoding.UTF8>), appelez.<xref:System.Text.Encoding.GetBytes%2A> pour tout d’abord transcoder la chaîne en un tableau d’octets encodé en UTF-8. Ensuite, transmettez- `Utf8JsonReader`le à.

Étant donné `Utf8JsonReader` que le considère que l’entrée est du texte JSON, une marque d’ordre d’octet (BOM) UTF-8 est considérée comme un JSON non valide. L’appelant doit filtrer ce dernier avant de passer les données au lecteur.

Pour obtenir des exemples de code, consultez [use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Lecture avec ReadOnlySequence à plusieurs segments

Si votre entrée JSON est un [>\<d’octets ReadOnlySpan ](xref:System.ReadOnlySpan%601), chaque élément JSON est accessible à partir `ValueSpan` de la propriété sur le lecteur au fur et à mesure que vous parcourez la boucle de lecture. Toutefois, si votre entrée est un [>\<d’octets ReadOnlySequence](xref:System.Buffers.ReadOnlySequence%601) (ce qui est le résultat de la <xref:System.IO.Pipelines.PipeReader>lecture à partir d’un), certains éléments JSON peuvent chevaucher plusieurs segments de l' `ReadOnlySequence<byte>` objet. Ces éléments ne sont pas accessibles à <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> partir d’un bloc de mémoire contigu. Au lieu de cela, chaque fois que vous `ReadOnlySequence<byte>` avez un segment multiple comme <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> entrée, interrogez la propriété sur le lecteur pour déterminer comment accéder à l’élément JSON actuel. Voici un modèle recommandé :

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Utiliser ValueTextEquals pour les recherches de nom de propriété

N’utilisez <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> pas pour effectuer des comparaisons octet par octet en appelant <xref:System.MemoryExtensions.SequenceEqual%2A> pour les recherches de nom de propriété. Appelez <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> à la place, car cette méthode annule l’échappement des caractères échappés dans le JSON. Voici un exemple qui montre comment rechercher une propriété nommée « Name » :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Lire les valeurs NULL dans les types valeur Nullable

`Newtonsoft.Json`fournit des API qui <xref:System.Nullable%601>retournent `ReadAsBoolean`, telles que, `Null` `TokenType` qui gère un pour vous `bool?`en retournant un. Les `System.Text.Json` API intégrées retournent uniquement des types valeur n’acceptant pas les valeurs NULL. Par exemple, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> retourne un `bool`. Elle lève une exception si elle trouve `Null` dans le JSON. Les exemples suivants illustrent deux façons de gérer les valeurs NULL, l’une en retournant un type valeur Nullable et l’autre en retournant la valeur par défaut :

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Multi-ciblage

Si vous devez continuer à utiliser `Newtonsoft.Json` pour certains frameworks cibles, vous pouvez effectuer plusieurs cibles et avoir deux implémentations. Toutefois, cela n’est pas trivial et nécessiterait `#ifdefs` une duplication source. Une façon de partager autant de code que possible consiste à créer un `ref struct` wrapper autour `Utf8JsonReader` de `Newtonsoft.Json` `JsonTextReader`et. Ce wrapper unifie la surface d’exposition publique tout en isolant les différences de comportement. Cela vous permet d’isoler les modifications principalement à la construction du type, ainsi que de passer le nouveau type par référence. Il s’agit du modèle que la bibliothèque [Microsoft. extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) suit :

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter comparé à JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types `String`.NET `Int32`courants tels `DateTime`que, et. Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.

Les sections suivantes expliquent les modèles de programmation `Utf8JsonWriter`recommandés pour l’utilisation de.

### <a name="write-with-utf-8-text"></a>Écrire avec du texte UTF-8

Pour obtenir les meilleures performances possibles lors de l' `Utf8JsonWriter`utilisation de, écrivez les charges utiles JSON déjà encodées en tant que texte UTF-8 plutôt qu’en tant que chaînes UTF-16. Utilisez <xref:System.Text.Json.JsonEncodedText> pour mettre en cache et précoder des noms et des valeurs de propriété de chaîne connus comme statiques, et les transmettre au writer, plutôt que d’utiliser des littéraux de chaîne UTF-16. Cela est plus rapide que la mise en cache et l’utilisation des tableaux d’octets UTF-8.

Cette approche fonctionne également si vous devez effectuer des séquences d’échappement personnalisées. `System.Text.Json`ne vous permet pas de désactiver l’échappement lors de l’écriture d’une chaîne. Toutefois, vous pouvez transmettre votre propre option personnalisée <xref:System.Text.Encodings.Web.JavaScriptEncoder> à l’enregistreur, ou créer votre propre `JsonEncodedText` option qui utilise votre `JavascriptEncoder` pour effectuer l’échappement, puis écrire à la `JsonEncodedText` place de la chaîne. Pour plus d’informations, consultez [personnaliser l’encodage des caractères](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Écrire des valeurs brutes

La `Newtonsoft.Json` `WriteRawValue` méthode écrit un JSON brut dans lequel une valeur est attendue. <xref:System.Text.Json>n’a pas d’équivalent direct, mais voici une solution de contournement qui garantit que seul le JSON valide est écrit :

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Personnaliser l’échappement des caractères

Le paramètre [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) de `JsonTextWriter` propose des options permettant d’échapper tous les caractères non-ASCII **ou** les caractères HTML. Par défaut, `Utf8JsonWriter` place dans une séquence d’échappement tous les caractères non-ASCII **et** html. Cette séquence d’échappement est effectuée pour des raisons de sécurité de défense en profondeur. Pour spécifier une autre stratégie d’échappement, créez un <xref:System.Text.Encodings.Web.JavaScriptEncoder> et définissez <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>. Pour plus d’informations, consultez [personnaliser l’encodage des caractères](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Personnaliser le format JSON

`JsonTextWriter`inclut les paramètres suivants, pour lesquels `Utf8JsonWriter` n’a pas d’équivalent :

* [Mise en retrait](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) : spécifie le nombre de caractères à mettre en retrait. `Utf8JsonWriter`effectue toujours une mise en retrait à 2 caractères.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) : spécifie le caractère à utiliser pour la mise en retrait.  `Utf8JsonWriter`utilise toujours un espace blanc.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) : spécifie le caractère à utiliser pour entourer les valeurs de chaîne.  `Utf8JsonWriter`utilise toujours des guillemets doubles.
* [QUOTENAME](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) : spécifie si les noms de propriété doivent être placés entre guillemets.  `Utf8JsonWriter`les entourent toujours de guillemets.

Il n’existe aucune solution de contournement qui vous permettrait de personnaliser le `Utf8JsonWriter` JSON généré par à l’aide de ces méthodes.

### <a name="write-null-values"></a>Écrire des valeurs null

Pour écrire des valeurs NULL à `Utf8JsonWriter`l’aide de, appelez :

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>pour écrire une paire clé-valeur avec NULL comme valeur.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>pour écrire NULL comme élément d’un tableau JSON.

Pour une propriété de type chaîne, si la chaîne est <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> null <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> , et sont `WriteNull` équivalents à et `WriteNullValue`.

### <a name="write-timespan-uri-or-char-values"></a>Écrire les valeurs TimeSpan, Uri ou char

`JsonTextWriter`fournit `WriteValue` des méthodes pour les valeurs [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [URI](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)et [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) . `Utf8JsonWriter`n’a pas de méthode équivalente. Au lieu de cela, mettez en forme ces valeurs `ToString()`en tant que chaînes (en <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>appelant, par exemple) et appelez.

### <a name="multi-targeting"></a>Multi-ciblage

Si vous devez continuer à utiliser `Newtonsoft.Json` pour certains frameworks cibles, vous pouvez effectuer plusieurs cibles et avoir deux implémentations. Toutefois, cela n’est pas trivial et nécessiterait `#ifdefs` une duplication source. Une façon de partager autant de code que possible consiste à créer un wrapper autour `Utf8JsonWriter` de `Newtonsoft` `JsonTextWriter`et. Ce wrapper unifie la surface d’exposition publique tout en isolant les différences de comportement. Cela vous permet d’isoler les modifications principalement de la construction du type. La bibliothèque [Microsoft. extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) est la suivante :

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Ressources supplémentaires

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Jsonvue](system-text-json-overview.md)
* [Procédure d’utilisationSystem.Text.Json](system-text-json-how-to.md)
* [Guide pratique pour écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md)
* [Prise en charge des valeurs DateTime et DateTimeOffset dansSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonRéférence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
