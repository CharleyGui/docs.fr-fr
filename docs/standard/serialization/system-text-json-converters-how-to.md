---
title: Comment écrire des convertisseurs personnalisés pour la sérialisation JSON-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: e0b769d7bb6b336d226cd48de1932524c4d7e74d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811065"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="3439f-102">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON (marshaling) dans .NET</span><span class="sxs-lookup"><span data-stu-id="3439f-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="3439f-103">Cet article explique comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de <xref:System.Text.Json> noms.</span><span class="sxs-lookup"><span data-stu-id="3439f-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="3439f-104">Pour une introduction à `System.Text.Json` , consultez [comment sérialiser et désérialiser JSON dans .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="3439f-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="3439f-105">Un *convertisseur* est une classe qui convertit un objet ou une valeur vers et à partir de JSON.</span><span class="sxs-lookup"><span data-stu-id="3439f-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="3439f-106">L' `System.Text.Json` espace de noms contient des convertisseurs intégrés pour la plupart des types primitifs qui mappent aux primitives JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3439f-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="3439f-107">Vous pouvez écrire des convertisseurs personnalisés :</span><span class="sxs-lookup"><span data-stu-id="3439f-107">You can write custom converters:</span></span>

* <span data-ttu-id="3439f-108">Pour remplacer le comportement par défaut d’un convertisseur intégré.</span><span class="sxs-lookup"><span data-stu-id="3439f-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="3439f-109">Par exemple, vous pouvez souhaiter que `DateTime` les valeurs soient représentées par le format mm/jj/aaaa au lieu du format ISO 8601-1:2019 par défaut.</span><span class="sxs-lookup"><span data-stu-id="3439f-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="3439f-110">Pour prendre en charge un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3439f-110">To support a custom value type.</span></span> <span data-ttu-id="3439f-111">Par exemple, un `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="3439f-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="3439f-112">Vous pouvez également écrire des convertisseurs personnalisés pour personnaliser ou étendre `System.Text.Json` des fonctionnalités qui ne sont pas incluses dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="3439f-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="3439f-113">Les scénarios suivants sont abordés plus loin dans cet article :</span><span class="sxs-lookup"><span data-stu-id="3439f-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="3439f-114">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="3439f-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="3439f-115">[Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="3439f-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="3439f-116">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="3439f-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="3439f-117">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="3439f-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="3439f-118">Modèles de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="3439f-118">Custom converter patterns</span></span>

<span data-ttu-id="3439f-119">Il existe deux modèles pour créer un convertisseur personnalisé : le modèle de base et le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="3439f-119">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="3439f-120">Le modèle de fabrique est destiné aux convertisseurs qui gèrent le type `Enum` ou les génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="3439f-120">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="3439f-121">Le modèle de base concerne les types génériques non génériques et fermés.</span><span class="sxs-lookup"><span data-stu-id="3439f-121">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="3439f-122">Par exemple, les convertisseurs pour les types suivants requièrent le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="3439f-122">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="3439f-123">Voici quelques exemples de types qui peuvent être gérés par le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="3439f-123">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="3439f-124">Le modèle de base crée une classe qui peut gérer un type.</span><span class="sxs-lookup"><span data-stu-id="3439f-124">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="3439f-125">Le modèle de fabrique crée une classe qui détermine, au moment de l’exécution, le type spécifique requis et crée dynamiquement le convertisseur approprié.</span><span class="sxs-lookup"><span data-stu-id="3439f-125">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="3439f-126">Exemple de convertisseur de base</span><span class="sxs-lookup"><span data-stu-id="3439f-126">Sample basic converter</span></span>

<span data-ttu-id="3439f-127">L’exemple suivant est un convertisseur qui remplace la sérialisation par défaut d’un type de données existant.</span><span class="sxs-lookup"><span data-stu-id="3439f-127">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="3439f-128">Le convertisseur utilise le format mm/jj/aaaa pour les `DateTimeOffset` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3439f-128">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="3439f-129">Exemple de convertisseur de modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="3439f-129">Sample factory pattern converter</span></span>

<span data-ttu-id="3439f-130">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="3439f-130">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="3439f-131">Le code suit le modèle de fabrique, car le premier paramètre de type générique est `Enum` et le second est ouvert.</span><span class="sxs-lookup"><span data-stu-id="3439f-131">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="3439f-132">La `CanConvert` méthode retourne `true` uniquement pour un `Dictionary` avec deux paramètres génériques, le premier étant un `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="3439f-132">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="3439f-133">Le convertisseur interne obtient un convertisseur existant pour gérer le type fourni au moment de l’exécution pour `TValue` .</span><span class="sxs-lookup"><span data-stu-id="3439f-133">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="3439f-134">Le code précédent est identique à ce qui est affiché dans le [dictionnaire de prise en charge avec une clé non-chaîne](#support-dictionary-with-non-string-key) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="3439f-134">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="3439f-135">Étapes pour suivre le modèle de base</span><span class="sxs-lookup"><span data-stu-id="3439f-135">Steps to follow the basic pattern</span></span>

<span data-ttu-id="3439f-136">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="3439f-136">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="3439f-137">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverter%601> où `T` est le type à sérialiser et à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="3439f-137">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="3439f-138">Substituez la `Read` méthode pour désérialiser le JSON entrant et le convertir en type `T` .</span><span class="sxs-lookup"><span data-stu-id="3439f-138">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="3439f-139">Utilisez le <xref:System.Text.Json.Utf8JsonReader> passé à la méthode pour lire le JSON.</span><span class="sxs-lookup"><span data-stu-id="3439f-139">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="3439f-140">Substituez la `Write` méthode pour sérialiser l’objet entrant de type `T` .</span><span class="sxs-lookup"><span data-stu-id="3439f-140">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="3439f-141">Utilisez le <xref:System.Text.Json.Utf8JsonWriter> passé à la méthode pour écrire le JSON.</span><span class="sxs-lookup"><span data-stu-id="3439f-141">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="3439f-142">Substituez la `CanConvert` méthode uniquement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3439f-142">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="3439f-143">L’implémentation par défaut retourne `true` lorsque le type à convertir est de type `T` .</span><span class="sxs-lookup"><span data-stu-id="3439f-143">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="3439f-144">Par conséquent, les convertisseurs qui prennent en charge uniquement `T` le type n’ont pas besoin de substituer cette méthode.</span><span class="sxs-lookup"><span data-stu-id="3439f-144">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="3439f-145">Pour obtenir un exemple de convertisseur qui doit substituer cette méthode, consultez la section sur la [désérialisation polymorphe](#support-polymorphic-deserialization) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="3439f-145">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="3439f-146">Vous pouvez faire référence au [code source des convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) en tant qu’implémentations de référence pour l’écriture de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3439f-146">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="3439f-147">Étapes pour suivre le modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="3439f-147">Steps to follow the factory pattern</span></span>

<span data-ttu-id="3439f-148">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="3439f-148">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="3439f-149">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="3439f-149">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="3439f-150">Substituez la `CanConvert` méthode pour retourner la valeur true lorsque le type à convertir est un qui peut être géré par le convertisseur.</span><span class="sxs-lookup"><span data-stu-id="3439f-150">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="3439f-151">Par exemple, si le convertisseur est destiné à `List<T>` lui, il peut uniquement gérer `List<int>` , `List<string>` et `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="3439f-151">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="3439f-152">Substituez la `CreateConverter` méthode pour retourner une instance d’une classe de convertisseur qui gérera le type-conversion fourni au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3439f-152">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="3439f-153">Créez la classe de convertisseur `CreateConverter` instanciée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="3439f-153">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="3439f-154">Le modèle de fabrique est requis pour les génériques ouverts, car le code permettant de convertir un objet vers et à partir d’une chaîne n’est pas le même pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="3439f-154">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="3439f-155">Un convertisseur pour un type générique ouvert ( `List<T>` , par exemple) doit créer un convertisseur pour un type générique fermé ( `List<DateTime>` , par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3439f-155">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="3439f-156">Le code doit être écrit pour gérer chaque type de générique fermé que le convertisseur peut gérer.</span><span class="sxs-lookup"><span data-stu-id="3439f-156">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="3439f-157">Le `Enum` type est similaire à un type générique ouvert : un convertisseur pour `Enum` doit créer un convertisseur pour un spécifique `Enum` ( `WeekdaysEnum` , par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3439f-157">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="3439f-158">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="3439f-158">Error handling</span></span>

<span data-ttu-id="3439f-159">Si vous devez lever une exception dans le code de gestion des erreurs, envisagez de lever un <xref:System.Text.Json.JsonException> sans message.</span><span class="sxs-lookup"><span data-stu-id="3439f-159">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="3439f-160">Ce type d’exception crée automatiquement un message qui comprend le chemin d’accès à la partie du JSON qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3439f-160">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="3439f-161">Par exemple, l’instruction `throw new JsonException();` génère un message d’erreur comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3439f-161">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="3439f-162">Si vous fournissez un message (par exemple, `throw new JsonException("Error occurred")` , l’exception fournit toujours le chemin d’accès dans la <xref:System.Text.Json.JsonException.Path> propriété.</span><span class="sxs-lookup"><span data-stu-id="3439f-162">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="3439f-163">Inscrire un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="3439f-163">Register a custom converter</span></span>

<span data-ttu-id="3439f-164">*Inscrire* un convertisseur personnalisé pour que les `Serialize` méthodes et l' `Deserialize` utilisent.</span><span class="sxs-lookup"><span data-stu-id="3439f-164">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="3439f-165">Choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="3439f-165">Choose one of the following approaches:</span></span>

* <span data-ttu-id="3439f-166">Ajoutez une instance de la classe de convertisseur à la <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="3439f-166">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="3439f-167">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) aux propriétés qui requièrent le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3439f-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="3439f-168">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) à une classe ou un struct qui représente un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3439f-168">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="3439f-169">Exemple d’inscription-collection Converters</span><span class="sxs-lookup"><span data-stu-id="3439f-169">Registration sample - Converters collection</span></span>

<span data-ttu-id="3439f-170">Voici un exemple qui rend la <xref:System.ComponentModel.DateTimeOffsetConverter> valeur par défaut pour les propriétés de type <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="3439f-170">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="3439f-171">Supposons que vous sérialisez une instance du type suivant :</span><span class="sxs-lookup"><span data-stu-id="3439f-171">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="3439f-172">Voici un exemple de sortie JSON qui montre que le convertisseur personnalisé a été utilisé :</span><span class="sxs-lookup"><span data-stu-id="3439f-172">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="3439f-173">Le code suivant utilise la même approche pour désérialiser à l’aide du `DateTimeOffset` convertisseur personnalisé :</span><span class="sxs-lookup"><span data-stu-id="3439f-173">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="3439f-174">Exemple d’inscription-[JsonConverter] sur une propriété</span><span class="sxs-lookup"><span data-stu-id="3439f-174">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="3439f-175">Le code suivant sélectionne un convertisseur personnalisé pour la `Date` propriété :</span><span class="sxs-lookup"><span data-stu-id="3439f-175">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="3439f-176">Le code à sérialiser `WeatherForecastWithConverterAttribute` ne requiert pas l’utilisation de `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="3439f-176">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="3439f-177">Le code à désérialiser ne nécessite pas non plus l’utilisation de `Converters` :</span><span class="sxs-lookup"><span data-stu-id="3439f-177">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="3439f-178">Exemple d’inscription-[JsonConverter] sur un type</span><span class="sxs-lookup"><span data-stu-id="3439f-178">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="3439f-179">Voici le code qui crée un struct et lui applique l' `[JsonConverter]` attribut :</span><span class="sxs-lookup"><span data-stu-id="3439f-179">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="3439f-180">Voici le convertisseur personnalisé pour le struct précédent :</span><span class="sxs-lookup"><span data-stu-id="3439f-180">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="3439f-181">L' `[JsonConvert]` attribut sur le struct inscrit le convertisseur personnalisé comme valeur par défaut pour les propriétés de type `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="3439f-181">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="3439f-182">Le convertisseur est automatiquement utilisé sur la `TemperatureCelsius` propriété du type suivant lors de la sérialisation ou de la désérialisation de ce dernier :</span><span class="sxs-lookup"><span data-stu-id="3439f-182">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="3439f-183">Priorité d’inscription du convertisseur</span><span class="sxs-lookup"><span data-stu-id="3439f-183">Converter registration precedence</span></span>

<span data-ttu-id="3439f-184">Lors de la sérialisation ou de la désérialisation, un convertisseur est choisi pour chaque élément JSON dans l’ordre suivant, de la priorité la plus élevée à la plus faible :</span><span class="sxs-lookup"><span data-stu-id="3439f-184">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="3439f-185">`[JsonConverter]` appliqué à une propriété.</span><span class="sxs-lookup"><span data-stu-id="3439f-185">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="3439f-186">Convertisseur ajouté à la `Converters` collection.</span><span class="sxs-lookup"><span data-stu-id="3439f-186">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="3439f-187">`[JsonConverter]` appliqué à un type valeur personnalisé ou POCO.</span><span class="sxs-lookup"><span data-stu-id="3439f-187">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="3439f-188">Si plusieurs convertisseurs personnalisés pour un type sont inscrits dans la `Converters` collection, le premier convertisseur qui retourne la valeur true pour `CanConvert` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3439f-188">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="3439f-189">Un convertisseur intégré est choisi uniquement si aucun convertisseur personnalisé applicable n’est inscrit.</span><span class="sxs-lookup"><span data-stu-id="3439f-189">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="3439f-190">Exemples de convertisseurs pour les scénarios courants</span><span class="sxs-lookup"><span data-stu-id="3439f-190">Converter samples for common scenarios</span></span>

<span data-ttu-id="3439f-191">Les sections suivantes fournissent des exemples de convertisseurs qui traitent de certains scénarios courants que les fonctionnalités intégrées ne gèrent pas.</span><span class="sxs-lookup"><span data-stu-id="3439f-191">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="3439f-192">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="3439f-192">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="3439f-193">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="3439f-193">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="3439f-194">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="3439f-194">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)
* <span data-ttu-id="3439f-195">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="3439f-195">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="3439f-196">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="3439f-196">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="3439f-197">Lors de la désérialisation vers une propriété de type `object` , un `JsonElement` objet est créé.</span><span class="sxs-lookup"><span data-stu-id="3439f-197">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="3439f-198">Cela est dû au fait que le désérialiseur ne sait pas quel type CLR créer, et qu’il ne tente pas de deviner.</span><span class="sxs-lookup"><span data-stu-id="3439f-198">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="3439f-199">Par exemple, si une propriété JSON a la valeur « true », le désérialiseur ne déduit pas que la valeur est un `Boolean` et, si un élément a « 01/01/2019 », le désérialiseur ne déduit pas qu’il s’agit d’un `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="3439f-199">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="3439f-200">L’inférence de type peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="3439f-200">Type inference can be inaccurate.</span></span> <span data-ttu-id="3439f-201">Si le désérialiseur analyse un nombre JSON qui n’a pas de virgule décimale comme un `long` , cela peut entraîner des problèmes hors limites si la valeur a été sérialisée à l’origine en tant que `ulong` ou `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="3439f-201">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="3439f-202">L’analyse d’un nombre qui a une virgule décimale `double` peut perdre la précision si le nombre a été initialement sérialisé en tant que `decimal` .</span><span class="sxs-lookup"><span data-stu-id="3439f-202">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="3439f-203">Pour les scénarios qui requièrent l’inférence de type, le code suivant montre un convertisseur personnalisé pour les `object` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3439f-203">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="3439f-204">Le code convertit :</span><span class="sxs-lookup"><span data-stu-id="3439f-204">The code converts:</span></span>

* <span data-ttu-id="3439f-205">`true` et `false` pour `Boolean`</span><span class="sxs-lookup"><span data-stu-id="3439f-205">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="3439f-206">Nombres sans décimal pour `long`</span><span class="sxs-lookup"><span data-stu-id="3439f-206">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="3439f-207">Nombres avec un nombre décimal à `double`</span><span class="sxs-lookup"><span data-stu-id="3439f-207">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="3439f-208">Dates jusqu’à `DateTime`</span><span class="sxs-lookup"><span data-stu-id="3439f-208">Dates to `DateTime`</span></span>
* <span data-ttu-id="3439f-209">Chaînes à `string`</span><span class="sxs-lookup"><span data-stu-id="3439f-209">Strings to `string`</span></span>
* <span data-ttu-id="3439f-210">Tout le reste vers `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="3439f-210">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="3439f-211">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="3439f-211">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="3439f-212">Voici un exemple de type avec des `object` Propriétés :</span><span class="sxs-lookup"><span data-stu-id="3439f-212">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="3439f-213">L’exemple suivant de JSON à désérialiser contient des valeurs qui seront désérialisées en tant que `DateTime` , `long` et `string` :</span><span class="sxs-lookup"><span data-stu-id="3439f-213">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="3439f-214">Sans le convertisseur personnalisé, la désérialisation place un `JsonElement` dans chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="3439f-214">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="3439f-215">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient plus d’exemples de convertisseurs personnalisés qui gèrent la désérialisation des `object` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3439f-215">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="3439f-216">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="3439f-216">Support Dictionary with non-string key</span></span>

<span data-ttu-id="3439f-217">La prise en charge intégrée pour les collections de dictionnaires concerne `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="3439f-217">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="3439f-218">Autrement dit, la clé doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="3439f-218">That is, the key must be a string.</span></span> <span data-ttu-id="3439f-219">Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="3439f-219">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="3439f-220">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="3439f-220">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="3439f-221">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="3439f-221">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="3439f-222">Le convertisseur peut sérialiser et désérialiser la `TemperatureRanges` propriété de la classe suivante qui utilise les éléments suivants `Enum` :</span><span class="sxs-lookup"><span data-stu-id="3439f-222">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="3439f-223">La sortie JSON de la sérialisation ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3439f-223">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="3439f-224">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient des exemples de convertisseurs personnalisés qui gèrent des dictionnaires non-clés.</span><span class="sxs-lookup"><span data-stu-id="3439f-224">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="3439f-225">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="3439f-225">Support polymorphic deserialization</span></span>

<span data-ttu-id="3439f-226">Les fonctionnalités intégrées offrent une plage limitée de [sérialisation polymorphe](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mais aucune prise en charge de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="3439f-226">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="3439f-227">La désérialisation requiert un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3439f-227">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="3439f-228">Supposons, par exemple, que vous avez une `Person` classe de base abstraite, avec des `Employee` `Customer` classes dérivées et.</span><span class="sxs-lookup"><span data-stu-id="3439f-228">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="3439f-229">La désérialisation polymorphe signifie qu’au moment du design vous pouvez spécifier `Person` en tant que cible de désérialisation, et les `Customer` `Employee` objets et dans le JSON sont correctement désérialisés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3439f-229">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="3439f-230">Pendant la désérialisation, vous devez trouver des indices qui identifient le type requis dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="3439f-230">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="3439f-231">Les types d’indices disponibles varient en fonction de chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="3439f-231">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="3439f-232">Par exemple, une propriété de discriminateur peut être disponible ou vous devrez peut-être vous appuyer sur la présence ou l’absence d’une propriété particulière.</span><span class="sxs-lookup"><span data-stu-id="3439f-232">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="3439f-233">La version actuelle de `System.Text.Json` ne fournit pas d’attributs pour spécifier comment gérer les scénarios de désérialisation polymorphe, donc les convertisseurs personnalisés sont requis.</span><span class="sxs-lookup"><span data-stu-id="3439f-233">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="3439f-234">Le code suivant illustre une classe de base, deux classes dérivées et un convertisseur personnalisé pour eux.</span><span class="sxs-lookup"><span data-stu-id="3439f-234">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="3439f-235">Le convertisseur utilise une propriété de discriminateur pour effectuer une désérialisation polymorphe.</span><span class="sxs-lookup"><span data-stu-id="3439f-235">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="3439f-236">Le discriminateur de type ne figure pas dans les définitions de classe, mais il est créé au cours de la sérialisation et est lu pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="3439f-236">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="3439f-237">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="3439f-237">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="3439f-238">Le convertisseur peut désérialiser JSON qui a été créé à l’aide du même convertisseur pour sérialiser, par exemple :</span><span class="sxs-lookup"><span data-stu-id="3439f-238">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="3439f-239">Dans l’exemple précédent, le code de convertisseur lit et écrit chaque propriété manuellement.</span><span class="sxs-lookup"><span data-stu-id="3439f-239">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="3439f-240">Une alternative consiste à appeler `Deserialize` ou `Serialize` à effectuer une partie du travail.</span><span class="sxs-lookup"><span data-stu-id="3439f-240">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="3439f-241">Pour obtenir un exemple, consultez [cette publication StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="3439f-241">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="3439f-242">Prendre en charge l’aller-retour pour la pile\<T></span><span class="sxs-lookup"><span data-stu-id="3439f-242">Support round-trip for Stack\<T></span></span>

<span data-ttu-id="3439f-243">Si vous désérialisez une chaîne JSON dans un <xref:System.Collections.Generic.Stack%601> objet et que vous sérialisez ensuite cet objet, le contenu de la pile est dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="3439f-243">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="3439f-244">Ce comportement s’applique aux types et à l’interface suivants, ainsi qu’aux types définis par l’utilisateur qui dérivent de ceux-ci :</span><span class="sxs-lookup"><span data-stu-id="3439f-244">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="3439f-245">Pour prendre en charge la sérialisation et la désérialisation qui conservent l’ordre d’origine dans la pile, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="3439f-245">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="3439f-246">Le code suivant illustre un convertisseur personnalisé qui permet l’aller-retour vers et à partir d' `Stack<T>` objets :</span><span class="sxs-lookup"><span data-stu-id="3439f-246">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="3439f-247">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="3439f-247">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a><span data-ttu-id="3439f-248">Autres exemples de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="3439f-248">Other custom converter samples</span></span>

<span data-ttu-id="3439f-249">L’article [migrer de Newtonsoft.Json vers System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) contient des exemples supplémentaires de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3439f-249">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="3439f-250">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) du `System.Text.Json.Serialization` code source comprend d’autres exemples de convertisseurs personnalisés, tels que :</span><span class="sxs-lookup"><span data-stu-id="3439f-250">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="3439f-251">[Convertisseur Int32 qui convertit la valeur null en valeur 0 lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="3439f-251">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="3439f-252">[Convertisseur Int32 qui autorise les valeurs de chaîne et de nombre lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="3439f-252">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="3439f-253">[Convertisseur enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="3439f-253">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="3439f-254">[\<T>Convertisseur de liste qui accepte les données externes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="3439f-254">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="3439f-255">[Long [] convertisseur qui fonctionne avec une liste de nombres délimités par des virgules](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="3439f-255">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="3439f-256">Si vous devez créer un convertisseur qui modifie le comportement d’un convertisseur intégré existant, vous pouvez faire en sorte que [le code source du convertisseur existant](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) serve de point de départ pour la personnalisation.</span><span class="sxs-lookup"><span data-stu-id="3439f-256">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3439f-257">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3439f-257">Additional resources</span></span>

* <span data-ttu-id="3439f-258">[Code source pour les convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="3439f-258">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="3439f-259">Prise en charge des valeurs DateTime et DateTimeOffset dans System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3439f-259">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="3439f-260">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="3439f-260">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="3439f-261">Procédure d’utilisation System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3439f-261">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="3439f-262">Migration à partir de Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="3439f-262">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* <span data-ttu-id="3439f-263">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3439f-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="3439f-264">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="3439f-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
