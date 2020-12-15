---
title: Comment écrire des convertisseurs personnalisés pour la sérialisation JSON-.NET
description: Découvrez comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de System.Text.Json noms.
ms.date: 12/14/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 390438e3dca7a5d40dd9957090f498b495996e05
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513196"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="f6797-103">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON (marshaling) dans .NET</span><span class="sxs-lookup"><span data-stu-id="f6797-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="f6797-104">Cet article explique comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de <xref:System.Text.Json> noms.</span><span class="sxs-lookup"><span data-stu-id="f6797-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="f6797-105">Pour une introduction à `System.Text.Json` , consultez [comment sérialiser et désérialiser JSON dans .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="f6797-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="f6797-106">Un *convertisseur* est une classe qui convertit un objet ou une valeur vers et à partir de JSON.</span><span class="sxs-lookup"><span data-stu-id="f6797-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="f6797-107">L' `System.Text.Json` espace de noms contient des convertisseurs intégrés pour la plupart des types primitifs qui mappent aux primitives JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f6797-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="f6797-108">Vous pouvez écrire des convertisseurs personnalisés :</span><span class="sxs-lookup"><span data-stu-id="f6797-108">You can write custom converters:</span></span>

* <span data-ttu-id="f6797-109">Pour remplacer le comportement par défaut d’un convertisseur intégré.</span><span class="sxs-lookup"><span data-stu-id="f6797-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="f6797-110">Par exemple, vous souhaiterez peut-être que les `DateTime` valeurs soient représentées par le format mm/jj/aaaa.</span><span class="sxs-lookup"><span data-stu-id="f6797-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format.</span></span> <span data-ttu-id="f6797-111">Par défaut, ISO 8601-1:2019 est pris en charge, y compris le profil RFC 3339.</span><span class="sxs-lookup"><span data-stu-id="f6797-111">By default, ISO 8601-1:2019 is supported, including the RFC 3339 profile.</span></span> <span data-ttu-id="f6797-112">Pour plus d’informations, consultez [prise en charge des System.Text.Json valeurs DateTime et DateTimeOffset dans ](../datetime/system-text-json-support.md).</span><span class="sxs-lookup"><span data-stu-id="f6797-112">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>
* <span data-ttu-id="f6797-113">Pour prendre en charge un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6797-113">To support a custom value type.</span></span> <span data-ttu-id="f6797-114">Par exemple, un `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="f6797-114">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="f6797-115">Vous pouvez également écrire des convertisseurs personnalisés pour personnaliser ou étendre `System.Text.Json` des fonctionnalités qui ne sont pas incluses dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="f6797-115">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="f6797-116">Les scénarios suivants sont abordés plus loin dans cet article :</span><span class="sxs-lookup"><span data-stu-id="f6797-116">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f6797-117">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f6797-117">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f6797-118">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f6797-118">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f6797-119">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f6797-119">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f6797-120">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f6797-120">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f6797-121">[Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="f6797-121">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="f6797-122">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f6797-122">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f6797-123">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f6797-123">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="f6797-124">Dans le code que vous écrivez pour un convertisseur personnalisé, vous devez être conscient de la baisse significative des performances pour l’utilisation de nouvelles <xref:System.Text.Json.JsonSerializerOptions> instances.</span><span class="sxs-lookup"><span data-stu-id="f6797-124">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="f6797-125">Pour plus d’informations, consultez [réutiliser des instances JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="f6797-125">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="f6797-126">Modèles de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="f6797-126">Custom converter patterns</span></span>

<span data-ttu-id="f6797-127">Il existe deux modèles pour créer un convertisseur personnalisé : le modèle de base et le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="f6797-127">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="f6797-128">Le modèle de fabrique est destiné aux convertisseurs qui gèrent le type `Enum` ou les génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="f6797-128">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="f6797-129">Le modèle de base concerne les types génériques non génériques et fermés.</span><span class="sxs-lookup"><span data-stu-id="f6797-129">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="f6797-130">Par exemple, les convertisseurs pour les types suivants requièrent le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="f6797-130">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="f6797-131">Voici quelques exemples de types qui peuvent être gérés par le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="f6797-131">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="f6797-132">Le modèle de base crée une classe qui peut gérer un type.</span><span class="sxs-lookup"><span data-stu-id="f6797-132">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="f6797-133">Le modèle de fabrique crée une classe qui détermine, au moment de l’exécution, le type spécifique requis et crée dynamiquement le convertisseur approprié.</span><span class="sxs-lookup"><span data-stu-id="f6797-133">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="f6797-134">Exemple de convertisseur de base</span><span class="sxs-lookup"><span data-stu-id="f6797-134">Sample basic converter</span></span>

<span data-ttu-id="f6797-135">L’exemple suivant est un convertisseur qui remplace la sérialisation par défaut d’un type de données existant.</span><span class="sxs-lookup"><span data-stu-id="f6797-135">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="f6797-136">Le convertisseur utilise le format mm/jj/aaaa pour les `DateTimeOffset` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f6797-136">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="f6797-137">Exemple de convertisseur de modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="f6797-137">Sample factory pattern converter</span></span>

<span data-ttu-id="f6797-138">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="f6797-138">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="f6797-139">Le code suit le modèle de fabrique, car le premier paramètre de type générique est `Enum` et le second est ouvert.</span><span class="sxs-lookup"><span data-stu-id="f6797-139">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="f6797-140">La `CanConvert` méthode retourne `true` uniquement pour un `Dictionary` avec deux paramètres génériques, le premier étant un `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="f6797-140">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="f6797-141">Le convertisseur interne obtient un convertisseur existant pour gérer le type fourni au moment de l’exécution pour `TValue` .</span><span class="sxs-lookup"><span data-stu-id="f6797-141">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="f6797-142">Le code précédent est identique à ce qui est affiché dans le [dictionnaire de prise en charge avec une clé non-chaîne](#support-dictionary-with-non-string-key) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f6797-142">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="f6797-143">Étapes pour suivre le modèle de base</span><span class="sxs-lookup"><span data-stu-id="f6797-143">Steps to follow the basic pattern</span></span>

<span data-ttu-id="f6797-144">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="f6797-144">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="f6797-145">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverter%601> où `T` est le type à sérialiser et à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="f6797-145">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="f6797-146">Substituez la `Read` méthode pour désérialiser le JSON entrant et le convertir en type `T` .</span><span class="sxs-lookup"><span data-stu-id="f6797-146">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="f6797-147">Utilisez le <xref:System.Text.Json.Utf8JsonReader> passé à la méthode pour lire le JSON.</span><span class="sxs-lookup"><span data-stu-id="f6797-147">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span> <span data-ttu-id="f6797-148">Vous n’avez pas à vous soucier de la gestion des données partielles, car le sérialiseur transmet toutes les données de la portée JSON actuelle.</span><span class="sxs-lookup"><span data-stu-id="f6797-148">You don't have to worry about handling partial data, as the serializer passes all the data for the current JSON scope.</span></span> <span data-ttu-id="f6797-149">Par conséquent, il n’est pas nécessaire d’appeler <xref:System.Text.Json.Utf8JsonReader.Skip%2A> ou <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> ou de valider que <xref:System.Text.Json.Utf8JsonReader.Read%2A> retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="f6797-149">So it isn't necessary to call <xref:System.Text.Json.Utf8JsonReader.Skip%2A> or <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> or to validate that <xref:System.Text.Json.Utf8JsonReader.Read%2A> returns `true`.</span></span>
* <span data-ttu-id="f6797-150">Substituez la `Write` méthode pour sérialiser l’objet entrant de type `T` .</span><span class="sxs-lookup"><span data-stu-id="f6797-150">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="f6797-151">Utilisez le <xref:System.Text.Json.Utf8JsonWriter> passé à la méthode pour écrire le JSON.</span><span class="sxs-lookup"><span data-stu-id="f6797-151">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="f6797-152">Substituez la `CanConvert` méthode uniquement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f6797-152">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="f6797-153">L’implémentation par défaut retourne `true` lorsque le type à convertir est de type `T` .</span><span class="sxs-lookup"><span data-stu-id="f6797-153">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="f6797-154">Par conséquent, les convertisseurs qui prennent en charge uniquement `T` le type n’ont pas besoin de substituer cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f6797-154">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="f6797-155">Pour obtenir un exemple de convertisseur qui doit substituer cette méthode, consultez la section sur la [désérialisation polymorphe](#support-polymorphic-deserialization) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="f6797-155">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="f6797-156">Vous pouvez faire référence au [code source des convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) en tant qu’implémentations de référence pour l’écriture de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f6797-156">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="f6797-157">Étapes pour suivre le modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="f6797-157">Steps to follow the factory pattern</span></span>

<span data-ttu-id="f6797-158">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="f6797-158">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="f6797-159">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="f6797-159">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="f6797-160">Substituez la `CanConvert` méthode pour retourner la valeur true lorsque le type à convertir est un qui peut être géré par le convertisseur.</span><span class="sxs-lookup"><span data-stu-id="f6797-160">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="f6797-161">Par exemple, si le convertisseur est destiné à `List<T>` lui, il peut uniquement gérer `List<int>` , `List<string>` et `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="f6797-161">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="f6797-162">Substituez la `CreateConverter` méthode pour retourner une instance d’une classe de convertisseur qui gérera le type-conversion fourni au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6797-162">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="f6797-163">Créez la classe de convertisseur `CreateConverter` instanciée par la méthode.</span><span class="sxs-lookup"><span data-stu-id="f6797-163">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="f6797-164">Le modèle de fabrique est requis pour les génériques ouverts, car le code permettant de convertir un objet vers et à partir d’une chaîne n’est pas le même pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="f6797-164">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="f6797-165">Un convertisseur pour un type générique ouvert ( `List<T>` , par exemple) doit créer un convertisseur pour un type générique fermé ( `List<DateTime>` , par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f6797-165">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="f6797-166">Le code doit être écrit pour gérer chaque type de générique fermé que le convertisseur peut gérer.</span><span class="sxs-lookup"><span data-stu-id="f6797-166">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="f6797-167">Le `Enum` type est similaire à un type générique ouvert : un convertisseur pour `Enum` doit créer un convertisseur pour un spécifique `Enum` ( `WeekdaysEnum` , par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f6797-167">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="f6797-168">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="f6797-168">Error handling</span></span>

<span data-ttu-id="f6797-169">Le sérialiseur fournit une gestion spéciale pour les types d’exception <xref:System.Text.Json.JsonException> et <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="f6797-169">The serializer provides special handling for exception types <xref:System.Text.Json.JsonException> and <xref:System.NotSupportedException>.</span></span>

### <a name="jsonexception"></a><span data-ttu-id="f6797-170">JsonException</span><span class="sxs-lookup"><span data-stu-id="f6797-170">JsonException</span></span>

<span data-ttu-id="f6797-171">Si vous levez une exception `JsonException` sans message, le sérialiseur crée un message qui comprend le chemin d’accès à la partie du JSON à l’origine de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="f6797-171">If you throw a `JsonException` without a message, the serializer creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="f6797-172">Par exemple, l’instruction `throw new JsonException()` génère un message d’erreur comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f6797-172">For example, the statement `throw new JsonException()` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="f6797-173">Si vous fournissez un message (par exemple, `throw new JsonException("Error occurred")` , le sérialiseur définit toujours les <xref:System.Text.Json.JsonException.Path> <xref:System.Text.Json.JsonException.LineNumber> Propriétés, et <xref:System.Text.Json.JsonException.BytePositionInLine> .</span><span class="sxs-lookup"><span data-stu-id="f6797-173">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the serializer still sets the <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, and <xref:System.Text.Json.JsonException.BytePositionInLine> properties.</span></span>

### <a name="notsupportedexception"></a><span data-ttu-id="f6797-174">NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="f6797-174">NotSupportedException</span></span>

<span data-ttu-id="f6797-175">Si vous levez une `NotSupportedException` , vous recevez toujours les informations de chemin d’accès dans le message.</span><span class="sxs-lookup"><span data-stu-id="f6797-175">If you throw a `NotSupportedException`, you always get the path information in the message.</span></span> <span data-ttu-id="f6797-176">Si vous fournissez un message, les informations relatives au chemin d’accès sont ajoutées à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f6797-176">If you provide a message, the path information is appended to it.</span></span> <span data-ttu-id="f6797-177">Par exemple, l’instruction `throw new NotSupportedException("Error occurred.")` génère un message d’erreur comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f6797-177">For example, the statement `throw new NotSupportedException("Error occurred.")` produces an error message like the following example:</span></span>

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a><span data-ttu-id="f6797-178">Quand lever le type d’exception</span><span class="sxs-lookup"><span data-stu-id="f6797-178">When to throw which exception type</span></span>

<span data-ttu-id="f6797-179">Lorsque la charge utile JSON contient des jetons qui ne sont pas valides pour le type en cours de désérialisation, levez une `JsonException` .</span><span class="sxs-lookup"><span data-stu-id="f6797-179">When the JSON payload contains tokens that are not valid for the type being deserialized, throw a `JsonException`.</span></span>

<span data-ttu-id="f6797-180">Lorsque vous souhaitez interdire certains types, levez une `NotSupportedException` .</span><span class="sxs-lookup"><span data-stu-id="f6797-180">When you want to disallow certain types, throw a `NotSupportedException`.</span></span> <span data-ttu-id="f6797-181">Cette exception est ce que le sérialiseur lève automatiquement pour les types qui ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f6797-181">This exception is what the serializer automatically throws for types that are not supported.</span></span> <span data-ttu-id="f6797-182">Par exemple, `System.Type` n’est pas pris en charge pour des raisons de sécurité. par conséquent, une tentative de désérialisation entraîne une `NotSupportedException` .</span><span class="sxs-lookup"><span data-stu-id="f6797-182">For example, `System.Type` is not supported for security reasons, so an attempt to deserialize it results in a `NotSupportedException`.</span></span>

<span data-ttu-id="f6797-183">Vous pouvez lever d’autres exceptions si nécessaire, mais elles n’incluent pas automatiquement les informations de chemin d’accès JSON.</span><span class="sxs-lookup"><span data-stu-id="f6797-183">You can throw other exceptions as needed, but they don't automatically include JSON path information.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="f6797-184">Inscrire un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="f6797-184">Register a custom converter</span></span>

<span data-ttu-id="f6797-185">*Inscrire* un convertisseur personnalisé pour que les `Serialize` méthodes et l' `Deserialize` utilisent.</span><span class="sxs-lookup"><span data-stu-id="f6797-185">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="f6797-186">Choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6797-186">Choose one of the following approaches:</span></span>

* <span data-ttu-id="f6797-187">Ajoutez une instance de la classe de convertisseur à la <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="f6797-187">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="f6797-188">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) aux propriétés qui requièrent le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6797-188">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="f6797-189">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) à une classe ou un struct qui représente un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6797-189">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="f6797-190">Exemple d’inscription-collection Converters</span><span class="sxs-lookup"><span data-stu-id="f6797-190">Registration sample - Converters collection</span></span>

<span data-ttu-id="f6797-191">Voici un exemple qui rend la <xref:System.ComponentModel.DateTimeOffsetConverter> valeur par défaut pour les propriétés de type <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="f6797-191">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="f6797-192">Supposons que vous sérialisez une instance du type suivant :</span><span class="sxs-lookup"><span data-stu-id="f6797-192">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="f6797-193">Voici un exemple de sortie JSON qui montre que le convertisseur personnalisé a été utilisé :</span><span class="sxs-lookup"><span data-stu-id="f6797-193">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="f6797-194">Le code suivant utilise la même approche pour désérialiser à l’aide du `DateTimeOffset` convertisseur personnalisé :</span><span class="sxs-lookup"><span data-stu-id="f6797-194">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="f6797-195">Exemple d’inscription-[JsonConverter] sur une propriété</span><span class="sxs-lookup"><span data-stu-id="f6797-195">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="f6797-196">Le code suivant sélectionne un convertisseur personnalisé pour la `Date` propriété :</span><span class="sxs-lookup"><span data-stu-id="f6797-196">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="f6797-197">Le code à sérialiser `WeatherForecastWithConverterAttribute` ne requiert pas l’utilisation de `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="f6797-197">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="f6797-198">Le code à désérialiser ne nécessite pas non plus l’utilisation de `Converters` :</span><span class="sxs-lookup"><span data-stu-id="f6797-198">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="f6797-199">Exemple d’inscription-[JsonConverter] sur un type</span><span class="sxs-lookup"><span data-stu-id="f6797-199">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="f6797-200">Voici le code qui crée un struct et lui applique l' `[JsonConverter]` attribut :</span><span class="sxs-lookup"><span data-stu-id="f6797-200">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="f6797-201">Voici le convertisseur personnalisé pour le struct précédent :</span><span class="sxs-lookup"><span data-stu-id="f6797-201">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="f6797-202">L' `[JsonConvert]` attribut sur le struct inscrit le convertisseur personnalisé comme valeur par défaut pour les propriétés de type `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="f6797-202">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="f6797-203">Le convertisseur est automatiquement utilisé sur la `TemperatureCelsius` propriété du type suivant lors de la sérialisation ou de la désérialisation de ce dernier :</span><span class="sxs-lookup"><span data-stu-id="f6797-203">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="f6797-204">Priorité d’inscription du convertisseur</span><span class="sxs-lookup"><span data-stu-id="f6797-204">Converter registration precedence</span></span>

<span data-ttu-id="f6797-205">Lors de la sérialisation ou de la désérialisation, un convertisseur est choisi pour chaque élément JSON dans l’ordre suivant, de la priorité la plus élevée à la plus faible :</span><span class="sxs-lookup"><span data-stu-id="f6797-205">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="f6797-206">`[JsonConverter]` appliqué à une propriété.</span><span class="sxs-lookup"><span data-stu-id="f6797-206">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="f6797-207">Convertisseur ajouté à la `Converters` collection.</span><span class="sxs-lookup"><span data-stu-id="f6797-207">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="f6797-208">`[JsonConverter]` appliqué à un type valeur personnalisé ou POCO.</span><span class="sxs-lookup"><span data-stu-id="f6797-208">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="f6797-209">Si plusieurs convertisseurs personnalisés pour un type sont inscrits dans la `Converters` collection, le premier convertisseur qui retourne la valeur true pour `CanConvert` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f6797-209">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="f6797-210">Un convertisseur intégré est choisi uniquement si aucun convertisseur personnalisé applicable n’est inscrit.</span><span class="sxs-lookup"><span data-stu-id="f6797-210">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="f6797-211">Exemples de convertisseurs pour les scénarios courants</span><span class="sxs-lookup"><span data-stu-id="f6797-211">Converter samples for common scenarios</span></span>

<span data-ttu-id="f6797-212">Les sections suivantes fournissent des exemples de convertisseurs qui traitent de certains scénarios courants que les fonctionnalités intégrées ne gèrent pas.</span><span class="sxs-lookup"><span data-stu-id="f6797-212">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f6797-213">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f6797-213">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f6797-214">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f6797-214">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f6797-215">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f6797-215">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f6797-216">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="f6797-216">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f6797-217">[Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="f6797-217">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="f6797-218">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f6797-218">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f6797-219">[Prenez en charge l’aller- \<T> retour pour la pile](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="f6797-219">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="f6797-220">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="f6797-220">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="f6797-221">Lors de la désérialisation vers une propriété de type `object` , un `JsonElement` objet est créé.</span><span class="sxs-lookup"><span data-stu-id="f6797-221">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="f6797-222">Cela est dû au fait que le désérialiseur ne sait pas quel type CLR créer, et qu’il ne tente pas de deviner.</span><span class="sxs-lookup"><span data-stu-id="f6797-222">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="f6797-223">Par exemple, si une propriété JSON a la valeur « true », le désérialiseur ne déduit pas que la valeur est un `Boolean` et, si un élément a « 01/01/2019 », le désérialiseur ne déduit pas qu’il s’agit d’un `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f6797-223">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="f6797-224">L’inférence de type peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="f6797-224">Type inference can be inaccurate.</span></span> <span data-ttu-id="f6797-225">Si le désérialiseur analyse un nombre JSON qui n’a pas de virgule décimale comme un `long` , cela peut entraîner des problèmes hors limites si la valeur a été sérialisée à l’origine en tant que `ulong` ou `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="f6797-225">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="f6797-226">L’analyse d’un nombre qui a une virgule décimale `double` peut perdre la précision si le nombre a été initialement sérialisé en tant que `decimal` .</span><span class="sxs-lookup"><span data-stu-id="f6797-226">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="f6797-227">Pour les scénarios qui requièrent l’inférence de type, le code suivant montre un convertisseur personnalisé pour les `object` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f6797-227">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="f6797-228">Le code convertit :</span><span class="sxs-lookup"><span data-stu-id="f6797-228">The code converts:</span></span>

* <span data-ttu-id="f6797-229">`true` et `false` pour `Boolean`</span><span class="sxs-lookup"><span data-stu-id="f6797-229">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="f6797-230">Nombres sans décimal pour `long`</span><span class="sxs-lookup"><span data-stu-id="f6797-230">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="f6797-231">Nombres avec un nombre décimal à `double`</span><span class="sxs-lookup"><span data-stu-id="f6797-231">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="f6797-232">Dates jusqu’à `DateTime`</span><span class="sxs-lookup"><span data-stu-id="f6797-232">Dates to `DateTime`</span></span>
* <span data-ttu-id="f6797-233">Chaînes à `string`</span><span class="sxs-lookup"><span data-stu-id="f6797-233">Strings to `string`</span></span>
* <span data-ttu-id="f6797-234">Tout le reste vers `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="f6797-234">Everything else to `JsonElement`</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="f6797-235">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="f6797-235">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="f6797-236">Voici un exemple de type avec des `object` Propriétés :</span><span class="sxs-lookup"><span data-stu-id="f6797-236">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="f6797-237">L’exemple suivant de JSON à désérialiser contient des valeurs qui seront désérialisées en tant que `DateTime` , `long` et `string` :</span><span class="sxs-lookup"><span data-stu-id="f6797-237">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="f6797-238">Sans le convertisseur personnalisé, la désérialisation place un `JsonElement` dans chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="f6797-238">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="f6797-239">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient plus d’exemples de convertisseurs personnalisés qui gèrent la désérialisation des `object` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f6797-239">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="f6797-240">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="f6797-240">Support Dictionary with non-string key</span></span>

<span data-ttu-id="f6797-241">La prise en charge intégrée pour les collections de dictionnaires concerne `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="f6797-241">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="f6797-242">Autrement dit, la clé doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f6797-242">That is, the key must be a string.</span></span> <span data-ttu-id="f6797-243">Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="f6797-243">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="f6797-244">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="f6797-244">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="f6797-245">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="f6797-245">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="f6797-246">Le convertisseur peut sérialiser et désérialiser la `TemperatureRanges` propriété de la classe suivante qui utilise les éléments suivants `Enum` :</span><span class="sxs-lookup"><span data-stu-id="f6797-246">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="f6797-247">La sortie JSON de la sérialisation ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f6797-247">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="f6797-248">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de l' `System.Text.Json.Serialization` espace de noms contient des exemples de convertisseurs personnalisés qui gèrent des dictionnaires non-clés.</span><span class="sxs-lookup"><span data-stu-id="f6797-248">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="f6797-249">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="f6797-249">Support polymorphic deserialization</span></span>

<span data-ttu-id="f6797-250">Les fonctionnalités intégrées offrent une plage limitée de [sérialisation polymorphe](system-text-json-polymorphism.md) , mais aucune prise en charge de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-250">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="f6797-251">La désérialisation requiert un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6797-251">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="f6797-252">Supposons, par exemple, que vous avez une `Person` classe de base abstraite, avec des `Employee` `Customer` classes dérivées et.</span><span class="sxs-lookup"><span data-stu-id="f6797-252">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="f6797-253">La désérialisation polymorphe signifie qu’au moment du design vous pouvez spécifier `Person` en tant que cible de désérialisation, et les `Customer` `Employee` objets et dans le JSON sont correctement désérialisés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6797-253">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="f6797-254">Pendant la désérialisation, vous devez trouver des indices qui identifient le type requis dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="f6797-254">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="f6797-255">Les types d’indices disponibles varient en fonction de chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="f6797-255">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="f6797-256">Par exemple, une propriété de discriminateur peut être disponible ou vous devrez peut-être vous appuyer sur la présence ou l’absence d’une propriété particulière.</span><span class="sxs-lookup"><span data-stu-id="f6797-256">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="f6797-257">La version actuelle de `System.Text.Json` ne fournit pas d’attributs pour spécifier comment gérer les scénarios de désérialisation polymorphe, donc les convertisseurs personnalisés sont requis.</span><span class="sxs-lookup"><span data-stu-id="f6797-257">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="f6797-258">Le code suivant illustre une classe de base, deux classes dérivées et un convertisseur personnalisé pour eux.</span><span class="sxs-lookup"><span data-stu-id="f6797-258">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="f6797-259">Le convertisseur utilise une propriété de discriminateur pour effectuer une désérialisation polymorphe.</span><span class="sxs-lookup"><span data-stu-id="f6797-259">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="f6797-260">Le discriminateur de type ne figure pas dans les définitions de classe, mais il est créé au cours de la sérialisation et est lu pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-260">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="f6797-261">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="f6797-261">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="f6797-262">Le convertisseur peut désérialiser JSON qui a été créé à l’aide du même convertisseur pour sérialiser, par exemple :</span><span class="sxs-lookup"><span data-stu-id="f6797-262">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="f6797-263">Dans l’exemple précédent, le code de convertisseur lit et écrit chaque propriété manuellement.</span><span class="sxs-lookup"><span data-stu-id="f6797-263">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="f6797-264">Une alternative consiste à appeler `Deserialize` ou `Serialize` à effectuer une partie du travail.</span><span class="sxs-lookup"><span data-stu-id="f6797-264">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="f6797-265">Pour obtenir un exemple, consultez [cette publication StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="f6797-265">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="f6797-266">Aller-retour du support pour la pile\<T></span><span class="sxs-lookup"><span data-stu-id="f6797-266">Support round trip for Stack\<T></span></span>

<span data-ttu-id="f6797-267">Si vous désérialisez une chaîne JSON dans un <xref:System.Collections.Generic.Stack%601> objet et que vous sérialisez ensuite cet objet, le contenu de la pile est dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="f6797-267">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="f6797-268">Ce comportement s’applique aux types et à l’interface suivants, ainsi qu’aux types définis par l’utilisateur qui dérivent de ceux-ci :</span><span class="sxs-lookup"><span data-stu-id="f6797-268">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="f6797-269">Pour prendre en charge la sérialisation et la désérialisation qui conservent l’ordre d’origine dans la pile, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="f6797-269">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="f6797-270">Le code suivant illustre un convertisseur personnalisé qui permet l’aller-retour vers et à partir d' `Stack<T>` objets :</span><span class="sxs-lookup"><span data-stu-id="f6797-270">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="f6797-271">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="f6797-271">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="f6797-272">Traiter les valeurs Null</span><span class="sxs-lookup"><span data-stu-id="f6797-272">Handle null values</span></span>

<span data-ttu-id="f6797-273">Par défaut, le sérialiseur gère les valeurs NULL comme suit :</span><span class="sxs-lookup"><span data-stu-id="f6797-273">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="f6797-274">Pour les types et types référence <xref:System.Nullable%601> :</span><span class="sxs-lookup"><span data-stu-id="f6797-274">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="f6797-275">Elle ne passe pas `null` aux convertisseurs personnalisés lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-275">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="f6797-276">Elle ne passe pas `JsonTokenType.Null` aux convertisseurs personnalisés lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-276">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="f6797-277">Elle retourne une `null` instance lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-277">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="f6797-278">Il écrit `null` directement avec le writer sur la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-278">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="f6797-279">Pour les types valeur n’acceptant pas les valeurs NULL :</span><span class="sxs-lookup"><span data-stu-id="f6797-279">For non-nullable value types:</span></span>

  * <span data-ttu-id="f6797-280">Il passe `JsonTokenType.Null` aux convertisseurs personnalisés lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-280">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="f6797-281">(Si aucun convertisseur personnalisé n’est disponible, une `JsonException` exception est levée par le convertisseur interne pour le type.)</span><span class="sxs-lookup"><span data-stu-id="f6797-281">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="f6797-282">Ce comportement de gestion null est principalement pour optimiser les performances en ignorant un appel supplémentaire au convertisseur.</span><span class="sxs-lookup"><span data-stu-id="f6797-282">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="f6797-283">En outre, il évite les convertisseurs de forçage pour les types Nullable à vérifier `null` au début de chaque `Read` `Write` remplacement de méthode et.</span><span class="sxs-lookup"><span data-stu-id="f6797-283">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="f6797-284">Pour permettre à un convertisseur personnalisé de gérer `null` un type référence ou valeur, remplacez <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> pour retourner `true` , comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f6797-284">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="18":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="f6797-285">Autres exemples de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="f6797-285">Other custom converter samples</span></span>

<span data-ttu-id="f6797-286">L’article [migrer de Newtonsoft.Json vers System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) contient des exemples supplémentaires de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f6797-286">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="f6797-287">Le [dossier tests unitaires](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) du `System.Text.Json.Serialization` code source comprend d’autres exemples de convertisseurs personnalisés, tels que :</span><span class="sxs-lookup"><span data-stu-id="f6797-287">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="f6797-288">[Convertisseur Int32 qui convertit la valeur null en valeur 0 lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="f6797-288">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="f6797-289">[Convertisseur Int32 qui autorise les valeurs de chaîne et de nombre lors de la désérialisation](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="f6797-289">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="f6797-290">[Convertisseur enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="f6797-290">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="f6797-291">[\<T>Convertisseur de liste qui accepte les données externes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="f6797-291">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="f6797-292">[Long [] convertisseur qui fonctionne avec une liste de nombres délimités par des virgules](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="f6797-292">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="f6797-293">Si vous devez créer un convertisseur qui modifie le comportement d’un convertisseur intégré existant, vous pouvez faire en sorte que [le code source du convertisseur existant](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) serve de point de départ pour la personnalisation.</span><span class="sxs-lookup"><span data-stu-id="f6797-293">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f6797-294">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f6797-294">Additional resources</span></span>

* <span data-ttu-id="f6797-295">[Code source pour les convertisseurs intégrés](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="f6797-295">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="f6797-296">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="f6797-296">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f6797-297">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="f6797-297">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f6797-298">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="f6797-298">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f6797-299">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="f6797-299">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f6797-300">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="f6797-300">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f6797-301">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="f6797-301">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f6797-302">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="f6797-302">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f6797-303">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="f6797-303">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f6797-304">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="f6797-304">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f6797-305">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="f6797-305">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f6797-306">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="f6797-306">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f6797-307">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f6797-307">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f6797-308">Personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="f6797-308">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f6797-309">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="f6797-309">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f6797-310">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f6797-310">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f6797-311">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f6797-311">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f6797-312">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f6797-312">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
