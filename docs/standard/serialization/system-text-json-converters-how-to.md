---
title: ''
ms.date: ''
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords: []
ms.openlocfilehash: 69c11df8217ac6dbdddd98c550f084075b901ea6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703610"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>Comment écrire des convertisseurs personnalisés pour la sérialisation JSON (marshaling) dans .NET

Cet article explique comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de <xref:System.Text.Json> noms. Pour une introduction à `System.Text.Json` , consultez [comment sérialiser et désérialiser JSON dans .net](system-text-json-how-to.md).

Un *convertisseur* est une classe qui convertit un objet ou une valeur vers et à partir de JSON. L' `System.Text.Json` espace de noms contient des convertisseurs intégrés pour la plupart des types primitifs qui mappent aux primitives JavaScript. Vous pouvez écrire des convertisseurs personnalisés :

* Pour remplacer le comportement par défaut d’un convertisseur intégré. Par exemple, vous pouvez souhaiter que `DateTime` les valeurs soient représentées par le format mm/jj/aaaa au lieu du format ISO 8601-1:2019 par défaut.
* Pour prendre en charge un type valeur personnalisé. Par exemple, un `PhoneNumber` struct.

Vous pouvez également écrire des convertisseurs personnalisés pour personnaliser ou étendre `System.Text.Json` des fonctionnalités qui ne sont pas incluses dans la version actuelle. Les scénarios suivants sont abordés plus loin dans cet article :

* [Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).
* [Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).
* [Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).
* [Prendre en charge l’aller-retour pour la pile \< T>](#support-round-trip-for-stackt).

## <a name="custom-converter-patterns"></a>Modèles de convertisseurs personnalisés

Il existe deux modèles pour créer un convertisseur personnalisé : le modèle de base et le modèle de fabrique. Le modèle de fabrique est destiné aux convertisseurs qui gèrent le type `Enum` ou les génériques ouverts. Le modèle de base concerne les types génériques non génériques et fermés.  Par exemple, les convertisseurs pour les types suivants requièrent le modèle de fabrique :

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Voici quelques exemples de types qui peuvent être gérés par le modèle de base :

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

Le modèle de base crée une classe qui peut gérer un type. Le modèle de fabrique crée une classe qui détermine au moment de l’exécution le type spécifique requis et crée dynamiquement le convertisseur approprié.

## <a name="sample-basic-converter"></a>Exemple de convertisseur de base

L’exemple suivant est un convertisseur qui remplace la sérialisation par défaut d’un type de données existant. Le convertisseur utilise le format mm/jj/aaaa pour les `DateTimeOffset` Propriétés.

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Exemple de convertisseur de modèle de fabrique

Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` . Le code suit le modèle de fabrique, car le premier paramètre de type générique est `Enum` et le second est ouvert. La `CanConvert` méthode retourne `true` uniquement pour un `Dictionary` avec deux paramètres génériques, le premier étant un `Enum` type. Le convertisseur interne obtient un convertisseur existant pour gérer le type fourni au moment de l’exécution pour `TValue` .

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Le code précédent est identique à ce qui est affiché dans le [dictionnaire de prise en charge avec une clé non-chaîne](#support-dictionary-with-non-string-key) plus loin dans cet article.

## <a name="steps-to-follow-the-basic-pattern"></a>Étapes pour suivre le modèle de base

Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de base :

* Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverter%601> où `T` est le type à sérialiser et à désérialiser.
* Substituez la `Read` méthode pour désérialiser le JSON entrant et le convertir en type `T` . Utilisez le <xref:System.Text.Json.Utf8JsonReader> passé à la méthode pour lire le JSON.
* Substituez la `Write` méthode pour sérialiser l’objet entrant de type `T` . Utilisez le <xref:System.Text.Json.Utf8JsonWriter> passé à la méthode pour écrire le JSON.
* Substituez la `CanConvert` méthode uniquement si nécessaire. L’implémentation par défaut retourne `true` lorsque le type à convertir est de type `T` . Par conséquent, les convertisseurs qui prennent en charge uniquement `T` le type n’ont pas besoin de substituer cette méthode. Pour obtenir un exemple de convertisseur qui doit substituer cette méthode, consultez la section sur la [désérialisation polymorphe](#support-polymorphic-deserialization) plus loin dans cet article.

Vous pouvez faire référence au [code source des convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) en tant qu’implémentations de référence pour l’écriture de convertisseurs personnalisés.

## <a name="steps-to-follow-the-factory-pattern"></a>Étapes pour suivre le modèle de fabrique

Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de fabrique :

* Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Substituez la `CanConvert` méthode pour retourner la valeur true lorsque le type à convertir est un qui peut être géré par le convertisseur. Par exemple, si le convertisseur est destiné à `List<T>` lui, il peut uniquement gérer `List<int>` , `List<string>` et `List<DateTime>` .
* Substituez la `CreateConverter` méthode pour retourner une instance d’une classe de convertisseur qui gérera le type-conversion fourni au moment de l’exécution.
* Créez la classe de convertisseur `CreateConverter` instanciée par la méthode.

Le modèle de fabrique est requis pour les génériques ouverts, car le code permettant de convertir un objet vers et à partir d’une chaîne n’est pas le même pour tous les types. Un convertisseur pour un type générique ouvert ( `List<T>` , par exemple) doit créer un convertisseur pour un type générique fermé ( `List<DateTime>` , par exemple) en arrière-plan. Le code doit être écrit pour gérer chaque type de générique fermé que le convertisseur peut gérer.

Le `Enum` type est similaire à un type générique ouvert : un convertisseur pour `Enum` doit créer un convertisseur pour un spécifique `Enum` ( `WeekdaysEnum` , par exemple) en arrière-plan.

## <a name="error-handling"></a>Gestion des erreurs

Si vous devez lever une exception dans le code de gestion des erreurs, envisagez de lever un <xref:System.Text.Json.JsonException> sans message. Ce type d’exception crée automatiquement un message qui comprend le chemin d’accès à la partie du JSON qui a provoqué l’erreur. Par exemple, l’instruction `throw new JsonException();` génère un message d’erreur comme dans l’exemple suivant :

```
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Si vous fournissez un message (par exemple, `throw new JsonException("Error occurred")` , l’exception fournit toujours le chemin d’accès dans la <xref:System.Text.Json.JsonException.Path> propriété.

## <a name="register-a-custom-converter"></a>Inscrire un convertisseur personnalisé

*Inscrire* un convertisseur personnalisé pour que les `Serialize` méthodes et l' `Deserialize` utilisent. Choisissez l’une des approches suivantes :

* Ajoutez une instance de la classe de convertisseur à la <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.
* Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) aux propriétés qui requièrent le convertisseur personnalisé.
* Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) à une classe ou un struct qui représente un type valeur personnalisé.

## <a name="registration-sample---converters-collection"></a>Exemple d’inscription-collection Converters

Voici un exemple qui rend la <xref:System.ComponentModel.DateTimeOffsetConverter> valeur par défaut pour les propriétés de type <xref:System.DateTimeOffset> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

Supposons que vous sérialisez une instance du type suivant :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

Voici un exemple de sortie JSON qui montre que le convertisseur personnalisé a été utilisé :

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Le code suivant utilise la même approche pour désérialiser à l’aide du `DateTimeOffset` convertisseur personnalisé :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Exemple d’inscription-[JsonConverter] sur une propriété

Le code suivant sélectionne un convertisseur personnalisé pour la `Date` propriété :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

Le code à sérialiser `WeatherForecastWithConverterAttribute` ne requiert pas l’utilisation de `JsonSerializeOptions.Converters` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

Le code à désérialiser ne nécessite pas non plus l’utilisation de `Converters` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Exemple d’inscription-[JsonConverter] sur un type

Voici le code qui crée un struct et lui applique l' `[JsonConverter]` attribut :

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

Voici le convertisseur personnalisé pour le struct précédent :

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

L' `[JsonConvert]` attribut sur le struct inscrit le convertisseur personnalisé comme valeur par défaut pour les propriétés de type `Temperature` . Le convertisseur est automatiquement utilisé sur la `TemperatureCelsius` propriété du type suivant lors de la sérialisation ou de la désérialisation de ce dernier :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Priorité d’inscription du convertisseur

Lors de la sérialisation ou de la désérialisation, un convertisseur est choisi pour chaque élément JSON dans l’ordre suivant, de la priorité la plus élevée à la plus faible :

* `[JsonConverter]`appliqué à une propriété.
* Convertisseur ajouté à la `Converters` collection.
* `[JsonConverter]`appliqué à un type valeur personnalisé ou POCO.

Si plusieurs convertisseurs personnalisés pour un type sont inscrits dans la `Converters` collection, le premier convertisseur qui retourne la valeur true pour `CanConvert` est utilisé.

Un convertisseur intégré est choisi uniquement si aucun convertisseur personnalisé applicable n’est inscrit.

## <a name="converter-samples-for-common-scenarios"></a>Exemples de convertisseurs pour les scénarios courants

Les sections suivantes fournissent des exemples de convertisseurs qui traitent de certains scénarios courants que les fonctionnalités intégrées ne gèrent pas.

* [Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties)
* [Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key)
* [Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization)
* [Prendre en charge l’aller-retour pour la pile \< T>](#support-round-trip-for-stackt).

### <a name="deserialize-inferred-types-to-object-properties"></a>Désérialiser les types inférés en propriétés d’objet

Lors de la désérialisation vers une propriété de type `object` , un `JsonElement` objet est créé. Cela est dû au fait que le désérialiseur ne sait pas quel type CLR créer, et qu’il ne tente pas de deviner. Par exemple, si une propriété JSON a la valeur « true », le désérialiseur ne déduit pas que la valeur est un `Boolean` et, si un élément a « 01/01/2019 », le désérialiseur ne déduit pas qu’il s’agit d’un `DateTime` .

L’inférence de type peut être inexacte. Si le désérialiseur analyse un nombre JSON qui n’a pas de virgule décimale comme un `long` , cela peut entraîner des problèmes hors limites si la valeur a été sérialisée à l’origine en tant que `ulong` ou `BigInteger` . L’analyse d’un nombre qui a une virgule décimale `double` peut perdre la précision si le nombre a été initialement sérialisé en tant que `decimal` .

Pour les scénarios qui requièrent l’inférence de type, le code suivant montre un convertisseur personnalisé pour les `object` Propriétés. Le code convertit :

* `true`et `false` pour`Boolean`
* Nombres sans décimal pour`long`
* Nombres avec un nombre décimal à`double`
* Dates jusqu’à`DateTime`
* Chaînes à`string`
* Tout le reste vers`JsonElement`

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

Le code suivant inscrit le convertisseur :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

Voici un exemple de type avec des `object` Propriétés :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

L’exemple suivant de JSON à désérialiser contient des valeurs qui seront désérialisées en tant que `DateTime` , `long` et `string` :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Sans le convertisseur personnalisé, la désérialisation place un `JsonElement` dans chaque propriété.

Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient plus d’exemples de convertisseurs personnalisés qui gèrent la désérialisation des `object` Propriétés.

### <a name="support-dictionary-with-non-string-key"></a>Dictionnaire de prise en charge avec clé non-chaîne

La prise en charge intégrée pour les collections de dictionnaires concerne `Dictionary<string, TValue>` . Autrement dit, la clé doit être une chaîne. Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, un convertisseur personnalisé est requis.

Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Le code suivant inscrit le convertisseur :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

Le convertisseur peut sérialiser et désérialiser la `TemperatureRanges` propriété de la classe suivante qui utilise les éléments suivants `Enum` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

La sortie JSON de la sérialisation ressemble à l’exemple suivant :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient des exemples de convertisseurs personnalisés qui gèrent des dictionnaires non-clés.

### <a name="support-polymorphic-deserialization"></a>Prendre en charge la désérialisation polymorphe

Les fonctionnalités intégrées offrent une plage limitée de [sérialisation polymorphe](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mais aucune prise en charge de la désérialisation. La désérialisation requiert un convertisseur personnalisé.

Supposons, par exemple, que vous avez une `Person` classe de base abstraite, avec des `Employee` `Customer` classes dérivées et. La désérialisation polymorphe signifie qu’au moment du design vous pouvez spécifier `Person` en tant que cible de désérialisation, et les `Customer` `Employee` objets et dans le JSON sont correctement désérialisés au moment de l’exécution. Pendant la désérialisation, vous devez trouver des indices qui identifient le type requis dans le JSON. Les types d’indices disponibles varient en fonction de chaque scénario. Par exemple, une propriété de discriminateur peut être disponible ou vous devrez peut-être vous appuyer sur la présence ou l’absence d’une propriété particulière. La version actuelle de `System.Text.Json` ne fournit pas d’attributs pour spécifier comment gérer les scénarios de désérialisation polymorphe, donc les convertisseurs personnalisés sont requis.

Le code suivant illustre une classe de base, deux classes dérivées et un convertisseur personnalisé pour eux. Le convertisseur utilise une propriété de discriminateur pour effectuer une désérialisation polymorphe. Le discriminateur de type ne figure pas dans les définitions de classe, mais il est créé au cours de la sérialisation et est lu pendant la désérialisation.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

Le code suivant inscrit le convertisseur :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

Le convertisseur peut désérialiser JSON qui a été créé à l’aide du même convertisseur pour sérialiser, par exemple :

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

Dans l’exemple précédent, le code de convertisseur lit et écrit chaque propriété manuellement. Une alternative consiste à appeler `Deserialize` ou `Serialize` à effectuer une partie du travail. Pour obtenir un exemple, consultez [cette publication StackOverflow](https://stackoverflow.com/a/59744873/12509023).

### <a name="support-round-trip-for-stackt"></a>Prendre en charge l’aller-retour pour la pile \< T>

Si vous désérialisez une chaîne JSON dans un <xref:System.Collections.Generic.Stack%601> objet et que vous sérialisez ensuite cet objet, le contenu de la pile est dans l’ordre inverse. Ce comportement s’applique aux types et à l’interface suivants, ainsi qu’aux types définis par l’utilisateur qui dérivent de ceux-ci :

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

Pour prendre en charge la sérialisation et la désérialisation qui conservent l’ordre d’origine dans la pile, un convertisseur personnalisé est requis.

Le code suivant illustre un convertisseur personnalisé qui permet l’aller-retour vers et à partir d' `Stack<T>` objets :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

Le code suivant inscrit le convertisseur :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a>Autres exemples de convertisseurs personnalisés

L’article [migrer de Newtonsoft.Json vers System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) contient des exemples supplémentaires de convertisseurs personnalisés.

Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) du `System.Text.Json.Serialization` code source comprend d’autres exemples de convertisseurs personnalisés, tels que :

* [Convertisseur Int32 qui convertit la valeur null en valeur 0 lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Convertisseur Int32 qui autorise les valeurs de chaîne et de nombre lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Convertisseur enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [Répertorier les \<> le convertisseur qui accepte les données externes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] convertisseur qui fonctionne avec une liste de nombres délimités par des virgules](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

Si vous devez créer un convertisseur qui modifie le comportement d’un convertisseur intégré existant, vous pouvez faire en sorte que [le code source du convertisseur existant](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) serve de point de départ pour la personnalisation.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Code source pour les convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [Prise en charge des valeurs DateTime et DateTimeOffset dansSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Jsonvue](system-text-json-overview.md)
* [Procédure d’utilisationSystem.Text.Json](system-text-json-how-to.md)
* [Migration à partir deNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.JsonRéférence d’API](xref:System.Text.Json)
* [System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
