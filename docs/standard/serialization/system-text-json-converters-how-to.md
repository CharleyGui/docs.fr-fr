---
title: Comment écrire des convertisseurs personnalisés pour la sérialisation JSON-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 0f8b89ec7d7b1677de085631958b888e154aa4fa
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116709"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="d87cf-102">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON (marshaling) dans .NET</span><span class="sxs-lookup"><span data-stu-id="d87cf-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="d87cf-103">Cet article explique comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de noms <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="d87cf-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="d87cf-104">Pour une présentation de `System.Text.Json`, consultez [sérialisation et désérialisation de JSON dans .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="d87cf-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="d87cf-105">Un *convertisseur* est une classe qui convertit un objet ou une valeur vers et à partir de JSON.</span><span class="sxs-lookup"><span data-stu-id="d87cf-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="d87cf-106">L’espace de noms `System.Text.Json` possède des convertisseurs intégrés pour la plupart des types primitifs qui mappent aux primitives JavaScript.</span><span class="sxs-lookup"><span data-stu-id="d87cf-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="d87cf-107">Vous pouvez écrire des convertisseurs personnalisés :</span><span class="sxs-lookup"><span data-stu-id="d87cf-107">You can write custom converters:</span></span>

* <span data-ttu-id="d87cf-108">Pour remplacer le comportement par défaut d’un convertisseur intégré.</span><span class="sxs-lookup"><span data-stu-id="d87cf-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="d87cf-109">Par exemple, vous pouvez souhaiter que `DateTime` valeurs soient représentées par le format mm/jj/aaaa au lieu du format ISO 8601-1:2019 par défaut.</span><span class="sxs-lookup"><span data-stu-id="d87cf-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="d87cf-110">Pour prendre en charge un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-110">To support a custom value type.</span></span> <span data-ttu-id="d87cf-111">Par exemple, un struct `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="d87cf-112">Vous pouvez également écrire des convertisseurs personnalisés pour personnaliser ou étendre `System.Text.Json` avec une fonctionnalité non incluse dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="d87cf-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="d87cf-113">Les scénarios suivants sont abordés plus loin dans cet article :</span><span class="sxs-lookup"><span data-stu-id="d87cf-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="d87cf-114">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="d87cf-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="d87cf-115">[Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="d87cf-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="d87cf-116">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="d87cf-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="d87cf-117">Modèles de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="d87cf-117">Custom converter patterns</span></span>

<span data-ttu-id="d87cf-118">Il existe deux modèles pour créer un convertisseur personnalisé : le modèle de base et le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="d87cf-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="d87cf-119">Le modèle de fabrique est destiné aux convertisseurs qui gèrent les `Enum` de type ou les génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="d87cf-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="d87cf-120">Le modèle de base concerne les types génériques non génériques et fermés.</span><span class="sxs-lookup"><span data-stu-id="d87cf-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="d87cf-121">Par exemple, les convertisseurs pour les types suivants requièrent le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="d87cf-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="d87cf-122">Voici quelques exemples de types qui peuvent être gérés par le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="d87cf-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="d87cf-123">Le modèle de base crée une classe qui peut gérer un type.</span><span class="sxs-lookup"><span data-stu-id="d87cf-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="d87cf-124">Le modèle de fabrique crée une classe qui détermine au moment de l’exécution le type spécifique requis et crée dynamiquement le convertisseur approprié.</span><span class="sxs-lookup"><span data-stu-id="d87cf-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="d87cf-125">Exemple de convertisseur de base</span><span class="sxs-lookup"><span data-stu-id="d87cf-125">Sample basic converter</span></span>

<span data-ttu-id="d87cf-126">L’exemple suivant est un convertisseur qui remplace la sérialisation par défaut d’un type de données existant.</span><span class="sxs-lookup"><span data-stu-id="d87cf-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="d87cf-127">Le convertisseur utilise le format mm/jj/aaaa pour les propriétés `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="d87cf-128">Exemple de convertisseur de modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="d87cf-128">Sample factory pattern converter</span></span>

<span data-ttu-id="d87cf-129">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="d87cf-130">Le code suit le modèle de fabrique, car le premier paramètre de type générique est `Enum` et le second est ouvert.</span><span class="sxs-lookup"><span data-stu-id="d87cf-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="d87cf-131">La méthode `CanConvert` retourne `true` uniquement pour un `Dictionary` avec deux paramètres génériques, le premier étant un type `Enum`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="d87cf-132">Le convertisseur interne obtient un convertisseur existant pour gérer le type fourni au moment de l’exécution pour `TValue`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="d87cf-133">Le code précédent est identique à ce qui est affiché dans le [dictionnaire de prise en charge avec une clé non-chaîne](#support-dictionary-with-non-string-key) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="d87cf-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="d87cf-134">Étapes pour suivre le modèle de base</span><span class="sxs-lookup"><span data-stu-id="d87cf-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="d87cf-135">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="d87cf-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="d87cf-136">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverter%601> où `T` est le type à sérialiser et à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="d87cf-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="d87cf-137">Substituez la méthode `Read` pour désérialiser le JSON entrant et le convertir en type `T`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="d87cf-138">Utilisez la <xref:System.Text.Json.Utf8JsonReader> transmise à la méthode pour lire le JSON.</span><span class="sxs-lookup"><span data-stu-id="d87cf-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="d87cf-139">Substituez la méthode `Write` pour sérialiser l’objet entrant de type `T`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="d87cf-140">Utilisez le <xref:System.Text.Json.Utf8JsonWriter> qui est passé à la méthode pour écrire le JSON.</span><span class="sxs-lookup"><span data-stu-id="d87cf-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="d87cf-141">Substituez la méthode `CanConvert` uniquement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d87cf-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="d87cf-142">L’implémentation par défaut retourne `true` lorsque le type à convertir est de type `T`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="d87cf-143">Par conséquent, les convertisseurs qui prennent uniquement en charge le type `T` n’ont pas besoin de substituer cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d87cf-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="d87cf-144">Pour obtenir un exemple de convertisseur qui doit substituer cette méthode, consultez la section sur la [désérialisation polymorphe](#support-polymorphic-deserialization) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="d87cf-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="d87cf-145">Vous pouvez faire référence au [code source des convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) en tant qu’implémentations de référence pour l’écriture de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d87cf-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="d87cf-146">Étapes pour suivre le modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="d87cf-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="d87cf-147">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="d87cf-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="d87cf-148">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="d87cf-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="d87cf-149">Substituez la méthode `CanConvert` pour retourner la valeur true lorsque le type à convertir est un qui peut être géré par le convertisseur.</span><span class="sxs-lookup"><span data-stu-id="d87cf-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="d87cf-150">Par exemple, si le convertisseur est destiné à `List<T>` il peut uniquement gérer `List<int>`, `List<string>`et `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="d87cf-151">Substituez la méthode `CreateConverter` pour retourner une instance d’une classe de convertisseur qui gérera le type-conversion fourni au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d87cf-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="d87cf-152">Créez la classe de convertisseur instanciée par la méthode `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="d87cf-153">Le modèle de fabrique est requis pour les génériques ouverts, car le code permettant de convertir un objet vers et à partir d’une chaîne n’est pas le même pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="d87cf-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="d87cf-154">Un convertisseur pour un type générique ouvert (`List<T>`, par exemple) doit créer un convertisseur pour un type générique fermé (`List<DateTime>`, par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d87cf-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="d87cf-155">Le code doit être écrit pour gérer chaque type de générique fermé que le convertisseur peut gérer.</span><span class="sxs-lookup"><span data-stu-id="d87cf-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="d87cf-156">Le type de `Enum` est semblable à un type générique ouvert : un convertisseur pour `Enum` doit créer un convertisseur pour un `Enum` spécifique (`WeekdaysEnum`, par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d87cf-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="d87cf-157">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="d87cf-157">Error handling</span></span>

<span data-ttu-id="d87cf-158">Si vous devez lever une exception dans le code de gestion des erreurs, envisagez de lever une <xref:System.Text.Json.JsonException> sans message.</span><span class="sxs-lookup"><span data-stu-id="d87cf-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="d87cf-159">Ce type d’exception crée automatiquement un message qui comprend le chemin d’accès à la partie du JSON qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="d87cf-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="d87cf-160">Par exemple, l’instruction `throw new JsonException();` produit un message d’erreur comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d87cf-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="d87cf-161">Si vous fournissez un message (par exemple, `throw new JsonException("Error occurred")`, l’exception fournit toujours le chemin d’accès dans la propriété <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="d87cf-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="d87cf-162">Inscrire un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="d87cf-162">Register a custom converter</span></span>

<span data-ttu-id="d87cf-163">*Inscrire* un convertisseur personnalisé pour que les méthodes `Serialize` et `Deserialize` l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="d87cf-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="d87cf-164">Choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d87cf-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="d87cf-165">Ajoutez une instance de la classe de convertisseur à la collection <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d87cf-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="d87cf-166">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) aux propriétés qui requièrent le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="d87cf-167">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) à une classe ou un struct qui représente un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="d87cf-168">Exemple d’inscription-collection Converters</span><span class="sxs-lookup"><span data-stu-id="d87cf-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="d87cf-169">Voici un exemple qui rend le <xref:System.ComponentModel.DateTimeOffsetConverter> par défaut pour les propriétés de type <xref:System.DateTimeOffset>:</span><span class="sxs-lookup"><span data-stu-id="d87cf-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="d87cf-170">Supposons que vous sérialisez une instance du type suivant :</span><span class="sxs-lookup"><span data-stu-id="d87cf-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="d87cf-171">Voici un exemple de sortie JSON qui montre que le convertisseur personnalisé a été utilisé :</span><span class="sxs-lookup"><span data-stu-id="d87cf-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="d87cf-172">Le code suivant utilise la même approche pour désérialiser à l’aide du convertisseur de `DateTimeOffset` personnalisé :</span><span class="sxs-lookup"><span data-stu-id="d87cf-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="d87cf-173">Exemple d’inscription-[JsonConverter] sur une propriété</span><span class="sxs-lookup"><span data-stu-id="d87cf-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="d87cf-174">Le code suivant sélectionne un convertisseur personnalisé pour la propriété `Date` :</span><span class="sxs-lookup"><span data-stu-id="d87cf-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="d87cf-175">Le code permettant de sérialiser `WeatherForecastWithConverterAttribute` ne requiert pas l’utilisation de `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="d87cf-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="d87cf-176">Le code à désérialiser ne nécessite pas non plus l’utilisation de `Converters`:</span><span class="sxs-lookup"><span data-stu-id="d87cf-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="d87cf-177">Exemple d’inscription-[JsonConverter] sur un type</span><span class="sxs-lookup"><span data-stu-id="d87cf-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="d87cf-178">Voici le code qui crée un struct et lui applique l’attribut `[JsonConverter]` :</span><span class="sxs-lookup"><span data-stu-id="d87cf-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="d87cf-179">Voici le convertisseur personnalisé pour le struct précédent :</span><span class="sxs-lookup"><span data-stu-id="d87cf-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="d87cf-180">L’attribut `[JsonConvert]` sur le struct inscrit le convertisseur personnalisé comme valeur par défaut pour les propriétés de type `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="d87cf-181">Le convertisseur est utilisé automatiquement sur la propriété `TemperatureCelsius` du type suivant lors de la sérialisation ou de la désérialisation de ce dernier :</span><span class="sxs-lookup"><span data-stu-id="d87cf-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="d87cf-182">Priorité d’inscription du convertisseur</span><span class="sxs-lookup"><span data-stu-id="d87cf-182">Converter registration precedence</span></span>

<span data-ttu-id="d87cf-183">Lors de la sérialisation ou de la désérialisation, un convertisseur est choisi pour chaque élément JSON dans l’ordre suivant, de la priorité la plus élevée à la plus faible :</span><span class="sxs-lookup"><span data-stu-id="d87cf-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="d87cf-184">`[JsonConverter]` appliquée à une propriété.</span><span class="sxs-lookup"><span data-stu-id="d87cf-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="d87cf-185">Convertisseur ajouté à la collection `Converters`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="d87cf-186">`[JsonConverter]` appliqué à un type valeur personnalisé ou POCO.</span><span class="sxs-lookup"><span data-stu-id="d87cf-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="d87cf-187">Si plusieurs convertisseurs personnalisés pour un type sont inscrits dans la collection `Converters`, le premier convertisseur qui retourne la valeur true pour `CanConvert` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="d87cf-188">Un convertisseur intégré est choisi uniquement si aucun convertisseur personnalisé applicable n’est inscrit.</span><span class="sxs-lookup"><span data-stu-id="d87cf-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="d87cf-189">Exemples de convertisseurs pour les scénarios courants</span><span class="sxs-lookup"><span data-stu-id="d87cf-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="d87cf-190">Les sections suivantes fournissent des exemples de convertisseurs qui traitent de certains scénarios courants que les fonctionnalités intégrées ne gèrent pas.</span><span class="sxs-lookup"><span data-stu-id="d87cf-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="d87cf-191">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="d87cf-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="d87cf-192">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="d87cf-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="d87cf-193">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="d87cf-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="d87cf-194">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="d87cf-194">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="d87cf-195">Lors de la désérialisation vers une propriété de type `object`, un objet `JsonElement` est créé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-195">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="d87cf-196">Cela est dû au fait que le désérialiseur ne sait pas quel type CLR créer, et qu’il ne tente pas de deviner.</span><span class="sxs-lookup"><span data-stu-id="d87cf-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="d87cf-197">Par exemple, si une propriété JSON a la valeur « true », le désérialiseur ne déduit pas que la valeur est un `Boolean`, et si un élément a « 01/01/2019 », le désérialiseur ne déduit pas qu’il s’agit d’un `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="d87cf-198">L’inférence de type peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="d87cf-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="d87cf-199">Si le désérialiseur analyse un nombre JSON qui n’a pas de virgule décimale comme `long`, cela peut entraîner des problèmes hors limites si la valeur a été sérialisée à l’origine en tant que `ulong` ou `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="d87cf-200">L’analyse d’un nombre qui a une virgule décimale comme `double` peut perdre la précision si le nombre a été initialement sérialisé en tant que `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="d87cf-201">Pour les scénarios qui requièrent l’inférence de type, le code suivant montre un convertisseur personnalisé pour les propriétés de `object`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-201">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="d87cf-202">Le code convertit :</span><span class="sxs-lookup"><span data-stu-id="d87cf-202">The code converts:</span></span>

* <span data-ttu-id="d87cf-203">`true` et `false` à `Boolean`</span><span class="sxs-lookup"><span data-stu-id="d87cf-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="d87cf-204">Nombres sans décimal pour `long`</span><span class="sxs-lookup"><span data-stu-id="d87cf-204">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="d87cf-205">Nombres avec un nombre décimal à `double`</span><span class="sxs-lookup"><span data-stu-id="d87cf-205">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="d87cf-206">Dates à `DateTime`</span><span class="sxs-lookup"><span data-stu-id="d87cf-206">Dates to `DateTime`</span></span>
* <span data-ttu-id="d87cf-207">Chaînes à `string`</span><span class="sxs-lookup"><span data-stu-id="d87cf-207">Strings to `string`</span></span>
* <span data-ttu-id="d87cf-208">Tout le reste à `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="d87cf-208">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="d87cf-209">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="d87cf-209">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="d87cf-210">Voici un exemple de type avec des propriétés de `object` :</span><span class="sxs-lookup"><span data-stu-id="d87cf-210">Here's an example type with `object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="d87cf-211">L’exemple suivant de JSON à désérialiser contient des valeurs qui seront désérialisées en tant que `DateTime`, `long`et `string`:</span><span class="sxs-lookup"><span data-stu-id="d87cf-211">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="d87cf-212">Sans le convertisseur personnalisé, la désérialisation place un `JsonElement` dans chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="d87cf-212">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="d87cf-213">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l’espace de noms `System.Text.Json.Serialization` contient plus d’exemples de convertisseurs personnalisés qui gèrent la désérialisation pour `object` propriétés.</span><span class="sxs-lookup"><span data-stu-id="d87cf-213">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="d87cf-214">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="d87cf-214">Support Dictionary with non-string key</span></span>

<span data-ttu-id="d87cf-215">La prise en charge intégrée pour les collections de dictionnaires concerne `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="d87cf-215">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="d87cf-216">Autrement dit, la clé doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d87cf-216">That is, the key must be a string.</span></span> <span data-ttu-id="d87cf-217">Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="d87cf-217">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="d87cf-218">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="d87cf-218">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="d87cf-219">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="d87cf-219">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="d87cf-220">Le convertisseur peut sérialiser et désérialiser la propriété `TemperatureRanges` de la classe suivante qui utilise le `Enum`suivant :</span><span class="sxs-lookup"><span data-stu-id="d87cf-220">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="d87cf-221">La sortie JSON de la sérialisation ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d87cf-221">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="d87cf-222">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l’espace de noms `System.Text.Json.Serialization` contient des exemples de convertisseurs personnalisés qui gèrent des dictionnaires non-clés.</span><span class="sxs-lookup"><span data-stu-id="d87cf-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="d87cf-223">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="d87cf-223">Support polymorphic deserialization</span></span>

<span data-ttu-id="d87cf-224">Les fonctionnalités intégrées offrent une plage limitée de [sérialisation polymorphe](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mais aucune prise en charge de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="d87cf-224">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="d87cf-225">La désérialisation requiert un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d87cf-225">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="d87cf-226">Supposons, par exemple, que vous avez une classe de base abstraite `Person`, avec `Employee` et `Customer` classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="d87cf-226">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="d87cf-227">La désérialisation polymorphe signifie qu’au moment du design vous pouvez spécifier `Person` comme cible de désérialisation, et les objets `Customer` et `Employee` dans le JSON sont correctement désérialisés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d87cf-227">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="d87cf-228">Pendant la désérialisation, vous devez trouver des indices qui identifient le type requis dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="d87cf-228">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="d87cf-229">Les types d’indices disponibles varient en fonction de chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="d87cf-229">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="d87cf-230">Par exemple, une propriété de discriminateur peut être disponible ou vous devrez peut-être vous appuyer sur la présence ou l’absence d’une propriété particulière.</span><span class="sxs-lookup"><span data-stu-id="d87cf-230">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="d87cf-231">La version actuelle de `System.Text.Json` ne fournit pas d’attributs pour spécifier comment gérer les scénarios de désérialisation polymorphe, donc les convertisseurs personnalisés sont requis.</span><span class="sxs-lookup"><span data-stu-id="d87cf-231">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="d87cf-232">Le code suivant illustre une classe de base, deux classes dérivées et un convertisseur personnalisé pour eux.</span><span class="sxs-lookup"><span data-stu-id="d87cf-232">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="d87cf-233">Le convertisseur utilise une propriété de discriminateur pour effectuer une désérialisation polymorphe.</span><span class="sxs-lookup"><span data-stu-id="d87cf-233">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="d87cf-234">Le discriminateur de type ne figure pas dans les définitions de classe, mais il est créé au cours de la sérialisation et est lu pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="d87cf-234">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="d87cf-235">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="d87cf-235">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="d87cf-236">Le convertisseur peut désérialiser JSON qui a été créé à l’aide du même convertisseur pour sérialiser, par exemple :</span><span class="sxs-lookup"><span data-stu-id="d87cf-236">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="d87cf-237">Dans l’exemple précédent, le code de convertisseur lit et écrit chaque propriété manuellement.</span><span class="sxs-lookup"><span data-stu-id="d87cf-237">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="d87cf-238">Une alternative consiste à appeler `Deserialize` ou `Serialize` pour effectuer une partie du travail.</span><span class="sxs-lookup"><span data-stu-id="d87cf-238">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="d87cf-239">Pour obtenir un exemple, consultez [cette publication StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="d87cf-239">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

## <a name="other-custom-converter-samples"></a><span data-ttu-id="d87cf-240">Autres exemples de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="d87cf-240">Other custom converter samples</span></span>

<span data-ttu-id="d87cf-241">L’article [migrer à partir de Newtonsoft. JSON vers System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md) contient des exemples supplémentaires de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d87cf-241">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="d87cf-242">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) dans le code source `System.Text.Json.Serialization` comprend d’autres exemples de convertisseurs personnalisés, tels que :</span><span class="sxs-lookup"><span data-stu-id="d87cf-242">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* [<span data-ttu-id="d87cf-243">Convertisseur Int32 qui convertit la valeur null en valeur 0 lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="d87cf-243">Int32 converter that converts null to 0 on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [<span data-ttu-id="d87cf-244">Convertisseur Int32 qui autorise les valeurs de chaîne et de nombre lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="d87cf-244">Int32 converter that allows both string and number values on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [<span data-ttu-id="d87cf-245">Convertisseur enum</span><span class="sxs-lookup"><span data-stu-id="d87cf-245">Enum converter</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [<span data-ttu-id="d87cf-246">Répertorier\<le convertisseur T > qui accepte les données externes</span><span class="sxs-lookup"><span data-stu-id="d87cf-246">List\<T> converter that accepts external data</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* <span data-ttu-id="d87cf-247">[Long [] convertisseur qui fonctionne avec une liste de nombres délimités par des virgules](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="d87cf-247">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span> 

<span data-ttu-id="d87cf-248">Si vous devez créer un convertisseur qui modifie le comportement d’un convertisseur intégré existant, vous pouvez faire en sorte que [le code source du convertisseur existant](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) serve de point de départ pour la personnalisation.</span><span class="sxs-lookup"><span data-stu-id="d87cf-248">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d87cf-249">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d87cf-249">Additional resources</span></span>

* [<span data-ttu-id="d87cf-250">Code source pour les convertisseurs intégrés</span><span class="sxs-lookup"><span data-stu-id="d87cf-250">Source code for built-in converters</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [<span data-ttu-id="d87cf-251">Prise en charge des valeurs DateTime et DateTimeOffset dans System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="d87cf-251">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="d87cf-252">Vue d’ensemble de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="d87cf-252">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d87cf-253">Utilisation de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="d87cf-253">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="d87cf-254">Migration à partir de Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="d87cf-254">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="d87cf-255">Informations de référence sur l’API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="d87cf-255">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="d87cf-256">Informations de référence sur l’API System. Text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="d87cf-256">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
