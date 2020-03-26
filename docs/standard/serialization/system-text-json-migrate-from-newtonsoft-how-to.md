---
title: Migrer de Newtonsoft.Json - System.Text.Json .NET
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
ms.openlocfilehash: 957bafcdf69d5792702962db6598458a0c8ec974
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291576"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Comment migrer de Newtonsoft.Json à System.Text.Json

Cet article montre comment migrer de <xref:System.Text.Json> [Newtonsoft.Json](https://www.newtonsoft.com/json) à .

L’espace `System.Text.Json` de nom fournit des fonctionnalités pour la sérialisation et le déséialisation de JavaScript Object Notation (JSON). La `System.Text.Json` bibliothèque est incluse dans le cadre partagé [.NET Core 3.0.](https://aka.ms/netcore3download) Pour d’autres cadres cibles, installez le paquet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet. Le paquet prend en charge :

* .NET Standard 2.0 et versions ultérieures
* .NET Framework 4.7.2 et versions ultérieures
* .NET Core 2.0, 2.1, et 2.2

`System.Text.Json`se concentre principalement sur la performance, la sécurité et la conformité aux normes. Il a quelques différences clés dans le comportement par défaut `Newtonsoft.Json`et ne vise pas à avoir la parité fonctionnalité avec . Pour certains scénarios, `System.Text.Json` n’a pas de fonctionnalité intégrée, mais il ya des solutions de contournement recommandées. Pour d’autres scénarios, les contournements sont impraticables. Si votre demande dépend d’une fonctionnalité manquante, envisagez [de déposer un problème](https://github.com/dotnet/runtime/issues/new) pour savoir si la prise en charge de votre scénario peut être ajoutée.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

La plupart de cet article <xref:System.Text.Json.JsonSerializer> est sur la façon d’utiliser l’API, mais il comprend également des conseils sur la façon d’utiliser le <xref:System.Text.Json.JsonDocument> (qui représente le modèle d’objet document ou DOM), <xref:System.Text.Json.Utf8JsonReader>, et <xref:System.Text.Json.Utf8JsonWriter> les types.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tableau des différences entre Newtonsoft.Json et System.Text.Json

Le tableau `Newtonsoft.Json` suivant `System.Text.Json` répertorie les caractéristiques et les équivalents. Les équivalents entrent dans les catégories suivantes :

* Pris en charge par la fonctionnalité intégrée. Obtenir un `System.Text.Json` comportement similaire peut nécessiter l’utilisation d’un attribut ou d’une option globale.
* Non pris en charge, la solution de contournement est possible. Les solutions de contournement sont [des convertisseurs personnalisés,](system-text-json-converters-how-to.md)qui peuvent ne pas fournir la parité complète avec `Newtonsoft.Json` la fonctionnalité. Pour certains d’entre eux, le code de l’échantillon est fourni à titre d’exemples. Si vous vous `Newtonsoft.Json` fiez à ces fonctionnalités, la migration nécessitera des modifications à vos modèles d’objets .NET ou à d’autres modifications de code.
* Non pris en charge, la solution de contournement n’est ni pratique ni possible. Si vous vous `Newtonsoft.Json` fiez à ces caractéristiques, la migration ne sera pas possible sans changements significatifs.

| Caractéristique de Newtonsoft.Json                               | System.Text.Json équivalent |
|-------------------------------------------------------|-----------------------------|
| Desération insensible par défaut           | ✔️ [PropertyNameCaseInsensitive global setting](#case-insensitive-deserialization) |
| Noms de propriété de chameau-cas                             | ✔️ [PropertyNamingPolicy cadre mondial](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Caractère minimal s’échappant                            | ✔️ caractère [strict s’échappant, configurable](#minimal-character-escaping) |
| `NullValueHandling.Ignore`cadre global             | ✔️ [IgnoreNullValues option mondiale](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Autoriser les commentaires                                        | ✔️ [ReadCommenthandling cadre mondial](#comments) |
| Autoriser les virgules de fuite                                 | ✔️ [AllowTrailingCommas cadre mondial](#trailing-commas) |
| Enregistrement de convertisseur personnalisé                         | ✔️ Ordre [de la préséance diffère](#converter-registration-precedence) |
| Pas de profondeur maximale par défaut                           | ✔️ Profondeur [maximale par défaut 64, configurable](#maximum-depth) |
| Soutien à un large éventail de types                    | ⚠️[Certains types nécessitent des convertisseurs personnalisés](#types-without-built-in-support) |
| Deserialiser les cordes comme des nombres                        | ⚠️[Non pris en charge, solution de contournement, échantillon](#quoted-numbers) |
| Désétérialiser `Dictionary` avec une clé non-corde          | ⚠️[Non pris en charge, solution de contournement, échantillon](#dictionary-with-non-string-key) |
| Sérialisation polymorphe                             | ⚠️[Non pris en charge, solution de contournement, échantillon](#polymorphic-serialization) |
| Désétérialisation polymorphe                           | ⚠️[Non pris en charge, solution de contournement, échantillon](#polymorphic-deserialization) |
| Désétérialiser le type `object` inféré aux propriétés      | ⚠️[Non pris en charge, solution de contournement, échantillon](#deserialization-of-object-properties) |
| Deserialiser JSON `null` littéral à des types de valeur non-nullable | ⚠️[Non pris en charge, solution de contournement, échantillon](#deserialize-null-to-non-nullable-type) |
| Deserialiser aux classes et aux structs immuables          | ⚠️[Non pris en charge, solution de contournement, échantillon](#deserialize-to-immutable-classes-and-structs) |
| Attribut `[JsonConstructor]`                         | ⚠️[Non pris en charge, solution de contournement, échantillon](#specify-constructor-to-use) |
| `Required`réglage `[JsonProperty]` sur l’attribut        | ⚠️[Non pris en charge, solution de contournement, échantillon](#required-properties) |
| `NullValueHandling`réglage `[JsonProperty]` sur l’attribut | ⚠️[Non pris en charge, solution de contournement, échantillon](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`réglage `[JsonProperty]` sur l’attribut | ⚠️[Non pris en charge, solution de contournement, échantillon](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`cadre global                 | ⚠️[Non pris en charge, solution de contournement, échantillon](#conditionally-ignore-a-property) |
| `DefaultContractResolver`d’exclure les propriétés       | ⚠️[Non pris en charge, solution de contournement, échantillon](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` paramètres   | ⚠️[Non pris en charge, solution de contournement, échantillon](#specify-date-format) |
| Rappels                                             | ⚠️[Non pris en charge, solution de contournement, échantillon](#callbacks) |
| Soutien aux domaines public et non public              | ⚠️[Non pris en charge, solution de contournement](#public-and-non-public-fields) |
| Soutien aux ensembles et aux adeurs de propriétés internes et privés | ⚠️[Non pris en charge, solution de contournement](#internal-and-private-property-setters-and-getters) |
| Méthode `JsonConvert.PopulateObject`                   | ⚠️[Non pris en charge, solution de contournement](#populate-existing-objects) |
| `ObjectCreationHandling`cadre global               | ⚠️[Non pris en charge, solution de contournement](#reuse-rather-than-replace-properties) |
| Ajouter aux collections sans setters                    | ⚠️[Non pris en charge, solution de contournement](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`cadre global           | ❌[Non pris en charge](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`cadre global                | ❌[Non pris en charge](#preserve-object-references-and-handle-loops) |
| Soutien `System.Runtime.Serialization` aux attributs | ❌[Non pris en charge](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`cadre global                | ❌[Non pris en charge](#missingmemberhandling) |
| Autoriser les noms de propriété sans guillemets                   | ❌[Non pris en charge](#json-strings-property-names-and-string-values) |
| Autoriser des citations uniques autour des valeurs de chaîne              | ❌[Non pris en charge](#json-strings-property-names-and-string-values) |
| Autoriser les valeurs JSON non-cordes pour les propriétés à cordes    | ❌[Non pris en charge](#non-string-values-for-string-properties) |

Il ne s’agit `Newtonsoft.Json` pas d’une liste exhaustive de fonctionnalités. La liste comprend de nombreux scénarios qui ont été demandés dans [les questions GitHub](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) ou [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) postes. Si vous implémentez une solution de contournement pour l’un des scénarios énumérés ici qui n’a pas actuellement de code d’échantillon, et si vous souhaitez partager votre solution, sélectionnez **cette page** dans la [section Commentaires](/dotnet/standard/serialization/system-text-json-migrate-from-newtonsoft-how-to#feedback) de cette page. Cela crée un numéro GitHub et l’énumère au bas de cette page.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Différences dans le comportement par défaut JsonSerializer par rapport à Newtonsoft.Json

<xref:System.Text.Json>est stricte par défaut et évite toute conjecture ou interprétation au nom de l’appelant, mettant l’accent sur le comportement déterministe. La bibliothèque est intentionnellement conçue de cette façon pour la performance et la sécurité. `Newtonsoft.Json`est flexible par défaut. Cette différence fondamentale dans la conception est à l’origine de nombreuses différences spécifiques suivantes dans le comportement par défaut.

### <a name="case-insensitive-deserialization"></a>Désétérialisation insensible aux cas

Pendant la désétérialisation, `Newtonsoft.Json` ne cas insensible nom de propriété correspondant par défaut. La <xref:System.Text.Json> valeur par défaut est sensible aux cas, ce qui donne de meilleures performances puisqu’il fait un match exact. Pour plus d’informations sur la façon de faire un jumelage insensible aux cas, voir [case-insensible propriété correspondant](system-text-json-how-to.md#case-insensitive-property-matching).

Si vous utilisez `System.Text.Json` indirectement en utilisant ASP.NET Core, vous n’avez pas besoin `Newtonsoft.Json`de faire quoi que ce soit pour obtenir un comportement comme . ASP.NET Core spécifie les paramètres pour les [noms de propriétés](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) à boîtier `System.Text.Json`de chameau et l’appariement insensible au cas lorsqu’il utilise.

### <a name="minimal-character-escaping"></a>Caractère minimal s’échappant

Pendant la `Newtonsoft.Json` sérialisation, est relativement permissif de laisser passer les personnages sans les échapper. Autrement dit, il ne les `\uxxxx` `xxxx` remplace pas par où est le point de code du personnage. Lorsqu’il leur échappe, il le `\` fait en émettant `"` un `\"`avant que le personnage (par exemple, devient ). <xref:System.Text.Json>échappe à plus de caractères par défaut pour fournir des protections de défense en profondeur contre le script inter-site (XSS) ou des attaques de divulgation d’informations et le fait en utilisant la séquence de six caractères. `System.Text.Json`échappe à tous les caractères non-ASCII par défaut, de sorte `StringEscapeHandling.EscapeNonAscii` que `Newtonsoft.Json`vous n’avez pas besoin de faire quoi que ce soit si vous utilisez dans . `System.Text.Json`échappe également aux caractères sensibles à HTML, par défaut. Pour plus d’informations sur `System.Text.Json` la façon de remplacer le comportement par défaut, voir [personnaliser l’encodage des personnages](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Commentaires

Pendant la désédicalisation, `Newtonsoft.Json` ignore les commentaires dans le JSON par défaut. La <xref:System.Text.Json> valeur par défaut est de jeter des exceptions pour les commentaires parce que la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les inclut pas. Pour plus d’informations sur la façon d’autoriser les commentaires, voir [Autoriser les commentaires et les virgules de suivi](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Virgules de suivi

Pendant la désétérialisation, `Newtonsoft.Json` ignore les virgules de fuite par défaut. Il ignore également plusieurs virgules de `[{"Color":"Red"},{"Color":"Green"},,]`fuite (par exemple, ). La <xref:System.Text.Json> valeur par défaut est de jeter des exceptions pour les virgules de fuite parce que la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les permet pas. Pour plus d’informations sur la façon de les accepter, `System.Text.Json` voir Autoriser les commentaires et les [virgules de fuite](system-text-json-how-to.md#allow-comments-and-trailing-commas). Il n’y a aucun moyen d’autoriser plusieurs virgules de fuite.

### <a name="converter-registration-precedence"></a>Préséance d’enregistrement des convertisseurs

La `Newtonsoft.Json` préséance d’enregistrement pour les convertisseurs personnalisés est la suivante :

* Attribut sur la propriété
* Attribut sur le type
* [Collection de convertisseurs](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Cette commande signifie qu’un `Converters` convertisseur personnalisé dans la collection est remplacé par un convertisseur qui est enregistré en appliquant un attribut au niveau du type. Ces deux enregistrements sont annulés par un attribut au niveau de la propriété.

La <xref:System.Text.Json> préséance d’enregistrement pour les convertisseurs personnalisés est différente :

* Attribut sur la propriété
* <xref:System.Text.Json.JsonSerializerOptions.Converters>Collection
* Attribut sur le type

La différence ici est qu’un `Converters` convertisseur personnalisé dans la collection remplace un attribut au niveau du type. L’intention derrière cet ordre de préséance est de faire des changements de temps de fonctionnement l’emporter sur les choix de conception-temps. Il n’y a aucun moyen de changer la préséance.

Pour plus d’informations sur l’inscription des convertisseurs personnalisés, consultez [Register un convertisseur personnalisé](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Profondeur maximale

`Newtonsoft.Json`n’a pas de limite de profondeur maximale par défaut. Pour <xref:System.Text.Json> il ya une limite par défaut de 64, <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>et il est configurable par le réglage .

### <a name="json-strings-property-names-and-string-values"></a>JSON cordes (noms de propriété et valeurs de cordes)

Pendant la désétérialisation, `Newtonsoft.Json` accepte les noms de propriété entourés de citations doubles, de citations simples, ou sans citations. Il accepte les valeurs de chaîne entourées de doubles citations ou de citations simples. Par exemple, `Newtonsoft.Json` accepte le JSON suivant :

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`n’accepte que les noms de propriété et les valeurs de chaîne en double citations parce que ce format est exigé par la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) et est le seul format considéré comme valide JSON.

Une valeur incluse dans des devis uniques se traduit par un [JsonException](xref:System.Text.Json.JsonException) avec le message suivant :

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Valeurs non-cordes pour les propriétés à cordes

`Newtonsoft.Json`accepte des valeurs non-cordes, telles qu’un `true` `false`nombre ou les littérals et, pour la désétérialisation aux propriétés de la chaîne de type. Voici un exemple de JSON qui `Newtonsoft.Json` désélise avec succès à la classe suivante:

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

`System.Text.Json`ne désélise pas les valeurs non-cordes dans les propriétés de cordes. Une valeur non-corde reçue pour un champ de cordes se traduit par un [JsonException](xref:System.Text.Json.JsonException) avec le message suivant :

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scénarios utilisant JsonSerializer qui nécessitent des solution de contournement

Les scénarios suivants ne sont pas pris en charge par des fonctionnalités intégrées, mais des solutions de contournement sont possibles. Les solutions de contournement sont [des convertisseurs personnalisés,](system-text-json-converters-how-to.md)qui peuvent ne pas fournir la parité complète avec `Newtonsoft.Json` la fonctionnalité. Pour certains d’entre eux, le code de l’échantillon est fourni à titre d’exemples. Si vous vous `Newtonsoft.Json` fiez à ces fonctionnalités, la migration nécessitera des modifications à vos modèles d’objets .NET ou à d’autres modifications de code.

### <a name="types-without-built-in-support"></a>Types sans soutien intégré

<xref:System.Text.Json>ne fournit pas de support intégré pour les types suivants :

* <xref:System.Data.DataTable>et les types connexes
* Types de F, tels que [les syndicats discriminés, les](../../fsharp/language-reference/discriminated-unions.md)types de [disques,](../../fsharp/language-reference/records.md)et [les types de dossiers anonymes](../../fsharp/language-reference/anonymous-records.md).
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>et ses types génériques associés

Les convertisseurs personnalisés peuvent être implémenté pour les types qui n’ont pas de support intégré.

### <a name="quoted-numbers"></a>Numéros cités

`Newtonsoft.Json`peut sérialiser ou déséialiser les nombres représentés par les cordes JSON (entourés de citations). Par exemple, il `{"DegreesCelsius":"23"}` peut `{"DegreesCelsius":23}`accepter: au lieu de . Pour activer <xref:System.Text.Json>ce comportement, implémenter un convertisseur personnalisé comme l’exemple suivant. Le convertisseur gère les `long`propriétés définies comme :

* Il les sérialis comme des cordes JSON.
* Il accepte les nombres et les chiffres JSON dans les citations tout en desérialisant.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Enregistrez ce convertisseur personnalisé [en utilisant un attribut](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) sur des propriétés individuelles `long` ou [en ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

### <a name="dictionary-with-non-string-key"></a>Dictionnaire avec la clé non-corde

`Newtonsoft.Json`prend en `Dictionary<TKey, TValue>`charge les collections de type . Le support intégré pour les <xref:System.Text.Json> collections `Dictionary<string, TValue>`de dictionnaires est limité à . C’est-à-dire que la clé doit être une chaîne.

Pour soutenir un dictionnaire avec un intégrier ou un autre type comme clé, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés.](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)

### <a name="polymorphic-serialization"></a>Sérialisation polymorphe

`Newtonsoft.Json`automatiquement ne sérialisation polymorphe. Pour plus d’informations sur les <xref:System.Text.Json>capacités de sérialisation polymorphes limitées de , voir [Les propriétés Serialize des classes dérivées](system-text-json-how-to.md#serialize-properties-of-derived-classes).

La solution de contournement décrite est de définir `object`les propriétés qui peuvent contenir des classes dérivées comme type . Si ce n’est pas possible, une autre `Write` option est de créer un convertisseur avec une méthode pour toute la hiérarchie de type héritage comme l’exemple dans [Comment écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Désétérialisation polymorphe

`Newtonsoft.Json`a `TypeNameHandling` un paramètre qui ajoute des métadonnées de nom de type à la JSON tout en sérialisant. Il utilise les métadonnées tout en désétalant pour faire la désétérialisation polymorphe. <xref:System.Text.Json>peut faire une gamme limitée de [sérialisation polymorphe,](system-text-json-how-to.md#serialize-properties-of-derived-classes) mais pas de désétérialisation polymorphe.

Pour soutenir la désétérialisation polymorphe, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés.](system-text-json-converters-how-to.md#support-polymorphic-deserialization)

### <a name="deserialization-of-object-properties"></a>Désédicalisation des propriétés d’objets

Quand `Newtonsoft.Json` deserialise <xref:System.Object>à , il:

* Infère le type de valeurs primitives dans `null`la charge utile `string` `long`JSON (autre que ) et renvoie le stocké , , `double` `boolean`, ou `DateTime` comme un objet en boîte. *Les valeurs primitives* sont des valeurs JSON `true`simples `false`telles `null`qu’un nombre JSON, une chaîne, , , ou .
* Retourne `JObject` une `JArray` ou pour des valeurs complexes dans la charge utile JSON. *Les valeurs complexes* sont les collections de`{}`paires de valeurs clés`[]`JSON dans des accolades ( ) ou des listes de valeurs entre parenthèses ( ). Les propriétés et les valeurs dans les accolades ou les supports peuvent avoir des propriétés ou des valeurs supplémentaires.
* Renvoie une référence nulle lorsque `null` la charge utile a le Littéral JSON.

<xref:System.Text.Json>stocke une `JsonElement` boîte pour des valeurs primitives <xref:System.Object>et complexes chaque fois que le deserializing à , par exemple:

* Propriété `object`.
* Une `object` valeur de dictionnaire.
* Une `object` valeur de tableau.
* Une `object`racine .

Cependant, `System.Text.Json` traite `null` la `Newtonsoft.Json` même chose que et renvoie `null` une référence nulle lorsque la charge utile a le Littéral JSON en elle.

Pour implémenter `object` l’inférence de type pour les propriétés, créez un convertisseur comme l’exemple dans [Comment écrire des convertisseurs personnalisés.](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)

### <a name="deserialize-null-to-non-nullable-type"></a>Déséialiser le type nul à non-nullable

`Newtonsoft.Json`ne jette pas d’exception dans le scénario suivant :

* `NullValueHandling`est réglé `Ignore`à , et
* Pendant la désétérialisation, le JSON contient une valeur nulle pour un type de valeur non annulable.

Dans le même <xref:System.Text.Json> scénario, ne jeter une exception. (Le réglage de <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>manutention nul correspondant est .)

Si vous possédez le type cible, la meilleure solution de contournement `int` est `int?`de rendre la propriété en question annulée (par exemple, changer pour ).

Une autre solution de contournement est de faire un convertisseur pour `DateTimeOffset` le type, comme l’exemple suivant qui gère les valeurs nulles pour les types:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Enregistrez ce convertisseur personnalisé [en utilisant un attribut sur la propriété](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) ou [en ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

**Note:** Le convertisseur précédent **gère les valeurs nulles différemment** des `Newtonsoft.Json` POCO qui spécifient les valeurs par défaut. Supposons, par exemple, que le code suivant représente votre objet cible :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Et supposons que le JSON suivant est déséialisé en utilisant le convertisseur précédent:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Après désédicalisation, `Date` la propriété a 1/1/0001 (`default(DateTimeOffset)`), c’est-à-dire, la valeur fixée dans le constructeur est écrasée. Compte tenu du même POCO et de JSON, `Newtonsoft.Json` la désétérialisation laisserait `Date` 1/1/2001 dans la propriété.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserialiser aux classes et aux structs immuables

`Newtonsoft.Json`peut déséialiser à des classes immuables et des structs parce qu’il peut utiliser des constructeurs qui ont des paramètres. <xref:System.Text.Json>ne prend en charge que les constructeurs publics sans paramètres. En tant que solution de contournement, vous pouvez appeler un constructeur avec des paramètres dans un convertisseur personnalisé.

Voici une structable immuable avec plusieurs paramètres constructeurs :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

Et voici un convertisseur qui sérialise et désélise cette struct:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Enregistrez ce convertisseur personnalisé en <xref:System.Text.Json.JsonSerializerOptions.Converters> ajoutant le [convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la collection.

Par exemple, un convertisseur similaire qui gère les propriétés génériques ouvertes, voir le [convertisseur intégré pour les paires de valeur clé](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Spécifier le constructeur à utiliser

L’attribut `Newtonsoft.Json` `[JsonConstructor]` vous permet de spécifier quel constructeur appeler lors de la désétération à un COCO. <xref:System.Text.Json>ne prend en charge que les constructeurs sans paramètres. En tant que solution de contournement, vous pouvez appeler n’importe quel constructeur dont vous avez besoin dans un convertisseur personnalisé. Voir l’exemple pour [Deserialize à des classes immuables et des structs](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Propriétés requises

Dans `Newtonsoft.Json`, vous spécifiez `Required` qu’une propriété est nécessaire en définissant sur l’attribut. `[JsonProperty]` `Newtonsoft.Json`fait exception si aucune valeur n’est reçue dans le JSON pour une propriété marquée au besoin.

<xref:System.Text.Json>ne jette pas une exception si aucune valeur n’est reçue pour l’une des propriétés du type cible. Par exemple, si `WeatherForecast` vous avez un cours :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Le JSON suivant est déséialisé sans erreur :

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Pour faire échouer la désétérialisation si aucune propriété n’est `Date` dans le JSON, implémentez un convertisseur personnalisé. Le code de convertisseur d’échantillon `Date` suivant jette une exception si la propriété n’est pas définie après la désétérialisation est terminée :

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Enregistrez ce convertisseur personnalisé [en utilisant un attribut sur la classe POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [en ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Si vous suivez ce modèle, ne passez pas dans l’objet d’options lorsque vous appelez <xref:System.Text.Json.JsonSerializer.Serialize%2A> de façon récursive ou <xref:System.Text.Json.JsonSerializer.Deserialize%2A>. L’objet d’options contient la <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> collection. Si vous le passez `Serialize` `Deserialize`à ou , le convertisseur personnalisé appelle en lui-même, ce qui rend une boucle infinie qui se traduit par une exception de débordement de pile. Si les options par défaut ne sont pas réalisables, créez une nouvelle instance des options avec les paramètres dont vous avez besoin. Cette approche sera lente puisque chaque nouvelle instance cache indépendamment.

Le code de conversion précédent est un exemple simplifié. Une logique supplémentaire serait nécessaire si vous avez besoin de gérer des attributs (tels que [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) ou différentes options (comme les encodeurs personnalisés). En outre, le code d’exemple ne gère pas les propriétés pour lesquelles une valeur par défaut est définie dans le constructeur. Et cette approche ne fait pas de distinction entre les scénarios suivants :

* Il manque une propriété au JSON.
* Une propriété pour un type non-nullable est présente dans le JSON, mais la `int`valeur est le défaut pour le type, comme zéro pour un .
* Une propriété pour un type de valeur nulle est présente dans le JSON, mais la valeur est nulle.

### <a name="conditionally-ignore-a-property"></a>Ignorer sous condition une propriété

`Newtonsoft.Json`a plusieurs façons d’ignorer sous condition une propriété sur la sérialisation ou la désétérialisation :

* `DefaultContractResolver`vous permet de sélectionner des propriétés à inclure ou à exclure, en fonction de critères arbitraires.
* Les `NullValueHandling` `DefaultValueHandling` paramètres `JsonSerializerSettings` et les paramètres sur vous permettent de spécifier que toutes les propriétés à valeur nulle ou à valeur par défaut doivent être ignorées.
* Les `NullValueHandling` `DefaultValueHandling` paramètres et `[JsonProperty]` les paramètres de l’attribut vous permettent de spécifier les propriétés individuelles qui doivent être ignorées lorsqu’elles sont définies à null ou la valeur par défaut.

<xref:System.Text.Json>fournit les moyens suivants d’omettre les propriétés tout en sérialisant :

* [L’attribut [JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) sur une propriété fait omet la propriété du JSON pendant la sérialisation.
* L’option globale [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) vous permet d’exclure toutes les propriétés à valeur nulle.
* L’option globale [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) vous permet d’exclure toutes les propriétés de lecture seulement.

Ces options ne vous permettent **pas** :

* Ignorer toutes les propriétés qui ont la valeur par défaut pour le type.
* Ignorer les propriétés sélectionnées qui ont la valeur par défaut pour le type.
* Ignorer les propriétés sélectionnées si leur valeur est nulle.
* Ignorer les propriétés sélectionnées en fonction de critères arbitraires évalués au moment de l’exécution.

Pour cette fonctionnalité, vous pouvez écrire un convertisseur personnalisé. Voici un échantillon de POCO et un convertisseur personnalisé pour cela qui illustre cette approche:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Le convertisseur `Summary` fait ometer la propriété de la sérialisation si sa valeur est nulle, une chaîne vide ou «N/A».

Enregistrez ce convertisseur personnalisé [en utilisant un attribut sur la classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [en ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Cette approche exige une logique supplémentaire si :

* Le POCO comprend des propriétés complexes.
* Vous devez gérer des `[JsonIgnore]` attributs tels que ou des options telles que les encodeurs personnalisés.

### <a name="specify-date-format"></a>Spécifier le format de date

`Newtonsoft.Json`fournit plusieurs façons de `DateTime` contrôler `DateTimeOffset` la façon dont les propriétés et les types sont sérialisés et désétérialisés :

* Le `DateTimeZoneHandling` paramètre peut être `DateTime` utilisé pour sérialiser toutes les valeurs comme dates UTC.
* Le `DateFormatString` paramètre et `DateTime` les convertisseurs peuvent être utilisés pour personnaliser le format des chaînes de dattes.

Dans <xref:System.Text.Json>, le seul format qui a intégré le soutien est ISO 8601-1:2019 depuis qu’il est largement adopté, sans ambiguïté, et fait des allers-retours avec précision. Pour utiliser n’importe quel autre format, créez un convertisseur personnalisé. Pour plus d’informations, voir [DateTime et DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Rappels

`Newtonsoft.Json`vous permet d’exécuter du code personnalisé à plusieurs points du processus de sérialisation ou de désétérialisation :

* OnDeserializing (en commençant à déséialiser un objet)
* OnDeserialized (lorsqu’il est fini de déséialiser un objet)
* OnSerializing (en commençant à sérialiser un objet)
* OnSerialized (lorsqu’il est terminé en sérialisation d’un objet)

Dans <xref:System.Text.Json>, vous pouvez simuler des rappels en écrivant un convertisseur personnalisé. L’exemple suivant montre un convertisseur personnalisé pour un POCO. Le convertisseur comprend du code qui affiche un `Newtonsoft.Json` message à chaque point qui correspond à un rappel.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Enregistrez ce convertisseur personnalisé [en utilisant un attribut sur la classe](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) ou [en ajoutant le convertisseur](system-text-json-converters-how-to.md#registration-sample---converters-collection) à la <xref:System.Text.Json.JsonSerializerOptions.Converters> collection.

Si vous utilisez un convertisseur personnalisé qui suit l’échantillon précédent :

* Le `OnDeserializing` code n’a pas accès à la nouvelle instance POCO. Pour manipuler la nouvelle instance du COCO au début de la désétérialisation, mettez ce code dans le constructeur du BCO.
* Ne passez pas dans l’objet options lors `Serialize` `Deserialize`de l’appel récursif ou . L’objet d’options contient la `Converters` collection. Si vous le passez `Serialize` `Deserialize`à ou , le convertisseur sera utilisé, ce qui rend une boucle infinie qui se traduit par une exception de débordement de pile.

### <a name="public-and-non-public-fields"></a>Domaines publics et non publics

`Newtonsoft.Json`peuvent sérialiser et déséialiser les champs ainsi que les propriétés. <xref:System.Text.Json>ne fonctionne qu’avec des biens publics. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="internal-and-private-property-setters-and-getters"></a>Setters et getters de propriété interne et privé

`Newtonsoft.Json`peut utiliser des ensembles de propriétés `JsonProperty` et des getters privés et internes via l’attribut. <xref:System.Text.Json>ne prend en charge que les setters publics. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="populate-existing-objects"></a>Peupler les objets existants

La `JsonConvert.PopulateObject` méthode `Newtonsoft.Json` en désélise un document JSON à une instance existante d’une classe, au lieu de créer une nouvelle instance. <xref:System.Text.Json>crée toujours une nouvelle instance du type cible en utilisant le constructeur public sans paramètres par défaut. Les convertisseurs personnalisés peuvent se déséialiser en une instance existante.

### <a name="reuse-rather-than-replace-properties"></a>Réutiliser plutôt que remplacer les propriétés

Le `Newtonsoft.Json` `ObjectCreationHandling` paramètre vous permet de spécifier que les objets dans les propriétés doivent être réutilisés plutôt que remplacés lors de la désétérialisation. <xref:System.Text.Json>remplace toujours les objets dans les propriétés.  Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

### <a name="add-to-collections-without-setters"></a>Ajouter aux collections sans setters

Pendant la désétérialisation, `Newtonsoft.Json` ajoute des objets à une collection même si la propriété n’a pas de setter. <xref:System.Text.Json>ignore les propriétés qui n’ont pas de setters. Les convertisseurs personnalisés peuvent fournir cette fonctionnalité.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scénarios que JsonSerializer ne prend actuellement pas en charge

Pour les scénarios suivants, les solutions de contournement ne sont pas pratiques ou possibles. Si vous vous `Newtonsoft.Json` fiez à ces caractéristiques, la migration ne sera pas possible sans changements significatifs.

### <a name="preserve-object-references-and-handle-loops"></a>Préserver les références d’objets et les boucles de poignée

Par défaut, `Newtonsoft.Json` sérialiss par valeur. Par exemple, si un objet contient deux propriétés qui contiennent une référence au même `Person` objet, les valeurs des propriétés de cet `Person` objet sont dupliquées dans le JSON.

`Newtonsoft.Json`a `PreserveReferencesHandling` un `JsonSerializerSettings` paramètre sur qui vous permet de sérialiser par référence:

* Une métadonnée d’identifiant est ajoutée au `Person` JSON créé pour le premier objet.
* Le JSON qui est `Person` créé pour le deuxième objet contient une référence à cet identifiant au lieu des valeurs de propriété.

`Newtonsoft.Json`a également `ReferenceLoopHandling` un paramètre qui vous permet d’ignorer les références circulaires plutôt que de jeter une exception.

<xref:System.Text.Json>ne prend en charge la sérialisation que par valeur et jette une exception pour les références circulaires.

### <a name="systemruntimeserialization-attributes"></a>Attributs System.Runtime.Serialization

<xref:System.Text.Json>ne prend pas en `System.Runtime.Serialization` charge les attributs de l’espace de nom, tels que `DataMemberAttribute` et `IgnoreDataMemberAttribute`.

### <a name="octal-numbers"></a>Numéros octal

`Newtonsoft.Json`traite les nombres avec un zéro de premier plan comme nombres octal. <xref:System.Text.Json>ne permet pas les zéros de premier plan parce que la spécification [RFC 8259](https://tools.ietf.org/html/rfc8259) ne les permet pas.

### <a name="missingmemberhandling"></a>Manque de gestion

`Newtonsoft.Json`peut être configuré pour lancer des exceptions pendant la désétérialisation si le JSON inclut les propriétés qui manquent dans le type cible. <xref:System.Text.Json>ignore les propriétés supplémentaires dans le JSON, sauf lorsque vous utilisez [l’attribut [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Il n’y a pas de solution de contournement pour la fonction de membre manquant.

### <a name="tracewriter"></a>TraceWriter (en)

`Newtonsoft.Json`vous permet de débocher `TraceWriter` en utilisant un pour afficher les journaux qui sont générés par la sérialisation ou la désétérialisation. <xref:System.Text.Json>ne fait pas l’enregistrement.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument et JsonElement comparés à JToken (comme JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>permet d’analyser et de construire un modèle d’objet document (DOM) lu **uniquement** à partir de charges utiles existantes de JSON. Le DOM offre un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge <xref:System.Text.Json.JsonElement> utile peuvent être consultés via le type. Le `JsonElement` type fournit des API pour convertir le texte JSON en types .NET communs. `JsonDocument`expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.

### <a name="jsondocument-is-idisposable"></a>JsonDocument est IDisposable

`JsonDocument`construit une vue en mémoire des données dans un tampon mis en commun. Par conséquent, `JArray` `Newtonsoft.Json`contrairement `JObject` `JsonDocument` ou à `IDisposable` partir, le type implémente et doit être utilisé à l’intérieur d’un bloc à l’aide.

Ne retournez un `JsonDocument` a de votre API que si vous souhaitez transférer la propriété à vie et céder la responsabilité à l’appelant. Dans la plupart des scénarios, ce n’est pas nécessaire. Si l’appelant a besoin de travailler avec <xref:System.Text.Json.JsonElement.Clone%2A> l’ensemble du document JSON, retourner le de la <xref:System.Text.Json.JsonDocument.RootElement%2A>, qui est un <xref:System.Text.Json.JsonElement>. Si l’appelant doit travailler avec un élément particulier dans <xref:System.Text.Json.JsonElement.Clone%2A> le <xref:System.Text.Json.JsonElement>document JSON, retournez le de cela . Si vous `RootElement` retournez le ou un `Clone`sous-élément directement sans faire un , `JsonElement` l’appelant ne sera pas en mesure d’accéder à la retournée après le `JsonDocument` qui possède, il est éliminé.

Voici un exemple qui vous oblige `Clone`à faire un :

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

Le code précédent `JsonElement` s’attend à un qui contient une `fileName` propriété. Il ouvre le fichier JSON et crée un `JsonDocument`. La méthode suppose que l’appelant veut travailler avec l’ensemble du document, de sorte qu’il retourne le `Clone` de la `RootElement`.

Si vous `JsonElement` recevez un sous-élément et que vous retournez `Clone` un sous-élément, il n’est pas nécessaire de retourner un sous-élément. L’appelant est chargé de `JsonDocument` maintenir en `JsonElement` vie le que le passage appartient à. Par exemple :

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument est lu uniquement

Le <xref:System.Text.Json> DOM ne peut pas ajouter, supprimer ou modifier les éléments JSON. Il est conçu de cette façon pour la performance et de réduire les allocations pour analyser les tailles communes de charge utile JSON (c’est-à-dire, < 1 Mo). Si votre scénario utilise actuellement un DOM modifiable, l’une des solutions de contournement suivantes pourrait être faisable :

* Pour construire `JsonDocument` un à partir de zéro (c’est-à-dire, sans passer dans une charge utile JSON existante à la `Parse` méthode), écrire le texte JSON en utilisant le `Utf8JsonWriter` et analyser la sortie de cela pour faire un nouveau `JsonDocument`.
* Pour modifier `JsonDocument`un existant , utilisez-le pour écrire du texte JSON, en faisant des `JsonDocument`modifications pendant que vous écrivez, et analyser la sortie de cela pour faire un nouveau .
* Pour fusionner les documents JSON `JObject.Merge` `JContainer.Merge` existants, `Newtonsoft.Json`équivalents aux API ou aux API de , voir [ce numéro GitHub](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement est une structure syndicale

`JsonDocument`expose le `RootElement` comme une <xref:System.Text.Json.JsonElement>propriété de type , qui est un syndicat, type de struct qui englobe tout élément JSON. `Newtonsoft.Json`utilise des types hiérarchiques dédiés comme, `JObject``JArray`, , `JToken`et ainsi de suite. `JsonElement`est ce que vous pouvez rechercher et énumérer plus, et vous pouvez utiliser `JsonElement` pour matérialiser les éléments JSON en types .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Comment rechercher un JsonDocument et JsonElement pour des sous-éléments

Recherches pour les jetons `JObject` `JArray` JSON à l’aide ou à partir `Newtonsoft.Json` ont tendance à être relativement rapide parce qu’ils sont des recherches dans certains dictionnaires. En comparaison, `JsonElement` les recherches nécessitent une recherche séquentielle des propriétés `TryGetProperty`et sont donc relativement lentes (par exemple lors de l’utilisation). <xref:System.Text.Json>est conçu pour minimiser le temps d’analyse initial plutôt que le temps de recherche. Par conséquent, utilisez les approches suivantes pour `JsonDocument` optimiser les performances lors de la recherche à travers un objet :

* Utilisez les enumérateurs intégrés (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> et <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) plutôt que de faire votre propre indexation ou boucles.
* Ne faites pas une recherche séquentielle dans `JsonDocument` `RootElement`l’ensemble à travers chaque propriété en utilisant . Au lieu de cela, recherchez des objets JSON imbriqués en fonction de la structure connue des données JSON. Par exemple, si vous êtes `Grade` à `Student` la recherche `Student` d’une propriété `Grade` dans les objets, bouclez les objets et obtenez la valeur de chacun, plutôt que de rechercher à travers tous les `JsonElement` objets à la recherche de `Grade` propriétés. Faire ce dernier se traduira par des passes inutiles sur les mêmes données.

Pour un exemple de code, voir [Utilisez JsonDocument pour l’accès aux données](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader comparé à JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>est un lecteur de haute performance, faible allocation, avant-seulement pour UTF-8 encodé texte JSON, lu à partir d’un [byte ReadOnlySpan\<>](xref:System.ReadOnlySpan%601) ou [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601). Il `Utf8JsonReader` s’agit d’un type de bas niveau qui peut être utilisé pour construire des parsers personnalisés et deserializers.

Les sections suivantes expliquent les `Utf8JsonReader`modèles de programmation recommandés pour l’utilisation .

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader est un réf struct

Parce `Utf8JsonReader` que le type est un *rétructuration*, il a [certaines limitations](../../csharp/language-reference/keywords/ref.md#ref-struct-types). Par exemple, il ne peut pas être stocké comme un champ sur une classe ou struct autres qu’une structure de ref. Pour atteindre des performances élevées, `ref struct` ce type doit être un car il a besoin de cacher l’entrée [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601), qui lui-même est une struct ref. En outre, ce type est mutable car il détient l’état. Par conséquent, **passez-le par ref** plutôt que par valeur. Le passer par valeur entraînerait une copie struct et les changements d’état ne seraient pas visibles par l’appelant. Cela diffère `Newtonsoft.Json` de `Newtonsoft.Json` `JsonTextReader` puisqu’il s’agit d’une classe. Pour plus d’informations sur la façon d’utiliser les structs ref, voir [Écrire le code CMD sûr et efficace](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Lire le texte de l’UTF-8

Pour obtenir les meilleures performances `Utf8JsonReader`possibles tout en utilisant les charges utiles JSON déjà codées sous forme de texte UTF-8 plutôt que comme des chaînes UTF-16. Pour un exemple de code, voir [les données de filtre à l’aide d’Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Lire avec un stream ou PipeReader

La `Utf8JsonReader` lecture de supports d’un UTF-8 codé [ReadOnlySpan\<byte>](xref:System.ReadOnlySpan%601) ou [ReadOnlySequence\<byte>](xref:System.Buffers.ReadOnlySequence%601) (qui est le résultat de la lecture d’un <xref:System.IO.Pipelines.PipeReader>).

Pour la lecture synchrone, vous pouvez lire la charge utile JSON jusqu’à la fin du flux dans un tableau de byte et passer que dans le lecteur. Pour la lecture d’une chaîne (qui est codée <xref:System.Text.Encoding.UTF8>sous le titre UTF-16), appelez .<xref:System.Text.Encoding.GetBytes%2A> d’abord transcoder la chaîne à un tableau d’encodé utF-8. Ensuite, passez cela `Utf8JsonReader`à la .

Étant `Utf8JsonReader` donné que l’entrée considère comme un texte JSON, une marque d’ordonnance d’byte UTF-8 (BOM) est considérée comme invalide JSON. L’appelant doit filtrer cela avant de transmettre les données au lecteur.

Pour des exemples de code, voir [Utilisez Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Lire avec multi-segment ReadOnlySequence

Si votre entrée JSON est un [byte\<ReadOnlySpan>](xref:System.ReadOnlySpan%601), chaque élément JSON peut être consulté à partir de la `ValueSpan` propriété sur le lecteur que vous passez par la boucle de lecture. Cependant, si votre entrée est un [Byte\<ReadOnlySequence>](xref:System.Buffers.ReadOnlySequence%601) (qui est le résultat de la lecture d’un <xref:System.IO.Pipelines.PipeReader>), certains éléments JSON peuvent chevaucher plusieurs segments de l’objet. `ReadOnlySequence<byte>` Ces éléments ne seraient <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> pas accessibles à partir d’un bloc de mémoire contigus. Au lieu de cela, `ReadOnlySequence<byte>` chaque fois que <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> vous avez un multi-segment comme entrée, sondage de la propriété sur le lecteur pour comprendre comment accéder à l’élément actuel JSON. Voici un modèle recommandé :

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

### <a name="use-valuetextequals-for-property-name-lookups"></a>Utilisez ValueTextEquals pour les examens de noms de propriété

Ne pas <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> utiliser pour faire des comparaisons byte-byte en appelant <xref:System.MemoryExtensions.SequenceEqual%2A> à des recherches de nom de propriété. Appelez <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> plutôt, parce que cette méthode ne dépayse pas tous les personnages qui sont échappés dans le JSON. Voici un exemple qui montre comment rechercher une propriété qui est nommée «nom»:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Lisez les valeurs nulles en types de valeur nulle

`Newtonsoft.Json`fournit des API <xref:System.Nullable%601>qui `ReadAsBoolean`reviennent , `Null` `TokenType` comme , qui `bool?`gère un pour vous en retournant un . Les `System.Text.Json` API intégrées ne renvoient que les types de valeur non annulables. Par exemple, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> `bool`renvoie un . Il jette une exception `Null` s’il trouve dans le JSON. Les exemples suivants montrent deux façons de gérer les nulls, l’un en retournant un type de valeur nul et l’autre en retournant la valeur par défaut :

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

Si vous devez continuer `Newtonsoft.Json` à utiliser pour certains cadres cibles, vous pouvez cibler plusieurs cibles et avoir deux implémentations. Cependant, ce n’est pas `#ifdefs` anodin et nécessiterait une certaine duplication et source. Une façon de partager autant de code `ref struct` que `Utf8JsonReader` possible `Newtonsoft.Json` `JsonTextReader`est de créer un emballage autour et . Cet emballage unifierait la surface publique tout en isolant les différences comportementales. Cela vous permet d’isoler les changements principalement à la construction du type, ainsi que de passer le nouveau type autour par référence. C’est le modèle que la bibliothèque [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) suit:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter comparé à JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>est une façon de haute performance d’écrire UTF-8 encodé `String` `Int32`texte `DateTime`JSON à partir de types .NET communs comme , et . L’auteur est un type de bas niveau qui peut être utilisé pour construire des sérigraphis personnalisés.

Les sections suivantes expliquent les `Utf8JsonWriter`modèles de programmation recommandés pour l’utilisation .

### <a name="write-with-utf-8-text"></a>Écrire avec le texte UTF-8

Pour obtenir les meilleures performances `Utf8JsonWriter`possibles tout en utilisant les charges utiles JSON déjà codées sous forme de texte UTF-8 plutôt que comme des chaînes UTF-16. Utilisez <xref:System.Text.Json.JsonEncodedText> pour mettre en cache et pré-encoder les noms et les valeurs connus de propriété de chaîne comme statiques, et les transmettre à l’auteur, plutôt que d’utiliser des littérals de cordes UTF-16. C’est plus rapide que la mise en cache et l’utilisation de tableaux d’etc.8.

Cette approche fonctionne également si vous avez besoin de faire l’évasion personnalisée. `System.Text.Json`ne vous laisse pas désactiver s’échapper tout en écrivant une chaîne. Cependant, vous pouvez passer dans <xref:System.Text.Encodings.Web.JavaScriptEncoder> votre propre coutume comme une `JsonEncodedText` option à `JavascriptEncoder` l’écrivain, ou créer `JsonEncodedText` votre propre qui utilise votre pour faire l’évasion, puis écrire le lieu de la chaîne. Pour plus d’informations, voir [Personnaliser l’encodage des caractères](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Écrire des valeurs brutes

La `Newtonsoft.Json` `WriteRawValue` méthode écrit JSON brut où une valeur est attendue. <xref:System.Text.Json>n’a pas d’équivalent direct, mais voici une solution de contournement qui garantit que seul JSON valide est écrit:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Personnaliser l’évasion de caractère

Le paramètre [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) des offres d’options `JsonTextWriter` pour échapper à tous les personnages non-ASCII **ou** des caractères HTML. Par défaut, `Utf8JsonWriter` échappe à tous les caractères non-ASCII **et** HTML. Cette évasion est faite pour des raisons de sécurité approfondies. Pour spécifier une <xref:System.Text.Encodings.Web.JavaScriptEncoder> politique <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>d’évasion différente, créez un et définissez . Pour plus d’informations, voir [Personnaliser l’encodage des caractères](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Personnaliser le format JSON

`JsonTextWriter`comprend les paramètres suivants, pour lesquels `Utf8JsonWriter` il n’a pas d’équivalent :

* [Indentation](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Specifie le nombre de caractères à en retrait. `Utf8JsonWriter`fait toujours l’indentation à 2 caractères.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Specifie le personnage à utiliser pour l’indentation.  `Utf8JsonWriter`utilise toujours l’espace blanc.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Specifie le personnage à utiliser pour entourer les valeurs de chaîne.  `Utf8JsonWriter`utilise toujours des citations doubles.
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Précise s’il faut ou non entourer les noms de propriété avec des citations.  `Utf8JsonWriter`les entoure toujours de citations.

Il n’y a pas de solutions de contournement qui vous permettraient de personnaliser le JSON produit par `Utf8JsonWriter` ces façons.

### <a name="write-null-values"></a>Écrire des valeurs nulles

Pour écrire des `Utf8JsonWriter`valeurs nulles en utilisant , appelez :

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>d’écrire une paire de valeur clé avec null comme valeur.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>d’écrire nul comme élément d’un tableau JSON.

Pour une propriété à cordes, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> si <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> la `WriteNull` chaîne `WriteNullValue`est nulle, et sont équivalents à et .

### <a name="write-timespan-uri-or-char-values"></a>Écrivez des valeurs Timespan, Uri ou char

`JsonTextWriter`fournit `WriteValue` des méthodes pour [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm), et les valeurs [de char.](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) `Utf8JsonWriter`n’a pas de méthodes équivalentes. Au lieu de cela, formater `ToString()`ces valeurs comme <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>des chaînes (en appelant , par exemple) et appeler .

### <a name="multi-targeting"></a>Multi-ciblage

Si vous devez continuer `Newtonsoft.Json` à utiliser pour certains cadres cibles, vous pouvez cibler plusieurs cibles et avoir deux implémentations. Cependant, ce n’est pas `#ifdefs` anodin et nécessiterait une certaine duplication et source. Une façon de partager autant de code que `Utf8JsonWriter` possible `Newtonsoft` `JsonTextWriter`est de créer un emballage autour et . Cet emballage unifierait la surface publique tout en isolant les différences comportementales. Cela vous permet d’isoler les changements principalement à la construction du type. [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) bibliothèque suit:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Ressources supplémentaires

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonAperçu](system-text-json-overview.md)
* [Comment utiliserSystem.Text.Json](system-text-json-how-to.md)
* [Guide pratique pour écrire des convertisseurs personnalisés](system-text-json-converters-how-to.md)
* [DateTime et DateTimeOffset support dansSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonRéférence API](xref:System.Text.Json)
* [System.Text.Json. Référence API de sérialisation](xref:System.Text.Json.Serialization)
