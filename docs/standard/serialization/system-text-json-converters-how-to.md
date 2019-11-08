---
title: Comment écrire des convertisseurs personnalisés pour la sérialisation JSON-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741891"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="06094-102">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON dans .NET</span><span class="sxs-lookup"><span data-stu-id="06094-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="06094-103">Cet article explique comment créer des convertisseurs personnalisés pour les classes de sérialisation JSON fournies dans l’espace de noms <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="06094-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="06094-104">Pour une présentation de `System.Text.Json`, consultez [sérialisation et désérialisation de JSON dans .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="06094-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="06094-105">Un *convertisseur* est une classe qui convertit un objet ou une valeur vers et à partir de JSON.</span><span class="sxs-lookup"><span data-stu-id="06094-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="06094-106">L’espace de noms `System.Text.Json` possède des convertisseurs intégrés pour la plupart des types primitifs qui mappent aux primitives JavaScript.</span><span class="sxs-lookup"><span data-stu-id="06094-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="06094-107">Vous pouvez écrire des convertisseurs personnalisés :</span><span class="sxs-lookup"><span data-stu-id="06094-107">You can write custom converters:</span></span>

* <span data-ttu-id="06094-108">Pour remplacer le comportement par défaut d’un convertisseur intégré.</span><span class="sxs-lookup"><span data-stu-id="06094-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="06094-109">Par exemple, vous pouvez souhaiter que `DateTime` valeurs soient représentées par le format mm/jj/aaaa au lieu du format ISO 8601-1:2019 par défaut.</span><span class="sxs-lookup"><span data-stu-id="06094-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="06094-110">Pour prendre en charge un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="06094-110">To support a custom value type.</span></span> <span data-ttu-id="06094-111">Par exemple, un struct `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="06094-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="06094-112">Vous pouvez également écrire des convertisseurs personnalisés pour étendre les `System.Text.Json` avec des fonctionnalités qui ne sont pas incluses dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="06094-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="06094-113">Les scénarios suivants sont abordés plus loin dans cet article :</span><span class="sxs-lookup"><span data-stu-id="06094-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="06094-114">[Désérialiser les types inférés en propriétés d’objet](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="06094-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="06094-115">[Dictionnaire de prise en charge avec clé non-chaîne](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="06094-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="06094-116">[Prendre en charge la désérialisation polymorphe](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="06094-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="06094-117">Modèles de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="06094-117">Custom converter patterns</span></span>

<span data-ttu-id="06094-118">Il existe deux modèles pour créer un convertisseur personnalisé : le modèle de base et le modèle de fabrique.</span><span class="sxs-lookup"><span data-stu-id="06094-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="06094-119">Le modèle de fabrique est destiné aux convertisseurs qui gèrent les `Enum` de type ou les génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="06094-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="06094-120">Le modèle de base concerne les types génériques non génériques et fermés.</span><span class="sxs-lookup"><span data-stu-id="06094-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="06094-121">Par exemple, les convertisseurs pour les types suivants requièrent le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="06094-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="06094-122">Voici quelques exemples de types qui peuvent être gérés par le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="06094-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="06094-123">Le modèle de base crée une classe qui peut gérer un type.</span><span class="sxs-lookup"><span data-stu-id="06094-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="06094-124">Le modèle de fabrique crée une classe qui détermine au moment de l’exécution le type spécifique requis et crée dynamiquement le convertisseur approprié.</span><span class="sxs-lookup"><span data-stu-id="06094-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="06094-125">Exemple de convertisseur de base</span><span class="sxs-lookup"><span data-stu-id="06094-125">Sample basic converter</span></span>

<span data-ttu-id="06094-126">L’exemple suivant est un convertisseur qui remplace la sérialisation par défaut d’un type de données existant.</span><span class="sxs-lookup"><span data-stu-id="06094-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="06094-127">Le convertisseur utilise le format mm/jj/aaaa pour les propriétés `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="06094-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="06094-128">Exemple de convertisseur de modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="06094-128">Sample factory pattern converter</span></span>

<span data-ttu-id="06094-129">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="06094-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="06094-130">Le code suit le modèle de fabrique, car le premier paramètre de type générique est `Enum` et le second est ouvert.</span><span class="sxs-lookup"><span data-stu-id="06094-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="06094-131">La méthode `CanConvert` retourne `true` uniquement pour un `Dictionary` avec deux paramètres génériques, le premier étant un type `Enum`.</span><span class="sxs-lookup"><span data-stu-id="06094-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="06094-132">Le convertisseur interne obtient un convertisseur existant pour gérer le type fourni au moment de l’exécution pour `TValue`.</span><span class="sxs-lookup"><span data-stu-id="06094-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="06094-133">Le code précédent est identique à ce qui est affiché dans le [dictionnaire de prise en charge avec une clé non-chaîne](#support-dictionary-with-non-string-key) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="06094-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="06094-134">Étapes pour suivre le modèle de base</span><span class="sxs-lookup"><span data-stu-id="06094-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="06094-135">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="06094-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="06094-136">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverter%601> où `T` est le type à sérialiser et à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="06094-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="06094-137">Substituez la méthode `Read` pour désérialiser le JSON entrant et le convertir en type `T`.</span><span class="sxs-lookup"><span data-stu-id="06094-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="06094-138">Utilisez la <xref:System.Text.Json.Utf8JsonReader> transmise à la méthode pour lire le JSON.</span><span class="sxs-lookup"><span data-stu-id="06094-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="06094-139">Substituez la méthode `Write` pour sérialiser l’objet entrant de type `T`.</span><span class="sxs-lookup"><span data-stu-id="06094-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="06094-140">Utilisez le <xref:System.Text.Json.Utf8JsonWriter> qui est passé à la méthode pour écrire le JSON.</span><span class="sxs-lookup"><span data-stu-id="06094-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="06094-141">Substituez la méthode `CanConvert` uniquement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="06094-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="06094-142">L’implémentation par défaut retourne `true` lorsque le type à convertir est `T`de type.</span><span class="sxs-lookup"><span data-stu-id="06094-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="06094-143">Par conséquent, les convertisseurs qui prennent uniquement en charge le type `T` n’ont pas besoin de substituer cette méthode.</span><span class="sxs-lookup"><span data-stu-id="06094-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="06094-144">Pour obtenir un exemple de convertisseur qui doit substituer cette méthode, consultez la section sur la [désérialisation polymorphe](#support-polymorphic-deserialization) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="06094-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="06094-145">Vous pouvez faire référence au [code source des convertisseurs intégrés](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) en tant qu’implémentations de référence pour l’écriture de convertisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="06094-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="06094-146">Étapes pour suivre le modèle de fabrique</span><span class="sxs-lookup"><span data-stu-id="06094-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="06094-147">Les étapes suivantes expliquent comment créer un convertisseur en suivant le modèle de fabrique :</span><span class="sxs-lookup"><span data-stu-id="06094-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="06094-148">Créez une classe qui dérive de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="06094-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="06094-149">Substituez la méthode `CanConvert` pour retourner la valeur true lorsque le type à convertir est un qui peut être géré par le convertisseur.</span><span class="sxs-lookup"><span data-stu-id="06094-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="06094-150">Par exemple, si le convertisseur est destiné à `List<T>` il peut uniquement gérer `List<int>`, `List<string>`et `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="06094-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="06094-151">Substituez la méthode `CreateConverter` pour retourner une instance d’une classe de convertisseur qui gérera le type-conversion fourni au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="06094-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="06094-152">Créez la classe de convertisseur instanciée par la méthode `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="06094-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="06094-153">Le modèle de fabrique est requis pour les génériques ouverts, car le code permettant de convertir un objet vers et à partir d’une chaîne n’est pas le même pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="06094-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="06094-154">Un convertisseur pour un type générique ouvert (`List<T>`, par exemple) doit créer un convertisseur pour un type générique fermé (`List<DateTime>`, par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="06094-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="06094-155">Le code doit être écrit pour gérer chaque type de générique fermé que le convertisseur peut gérer.</span><span class="sxs-lookup"><span data-stu-id="06094-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="06094-156">Le type de `Enum` est semblable à un type générique ouvert : un convertisseur pour `Enum` doit créer un convertisseur pour un `Enum` spécifique (`WeekdaysEnum`, par exemple) en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="06094-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="06094-157">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="06094-157">Error handling</span></span>

<span data-ttu-id="06094-158">Si vous devez lever une exception dans le code de gestion des erreurs, envisagez de lever une <xref:System.Text.Json.JsonException> sans message.</span><span class="sxs-lookup"><span data-stu-id="06094-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="06094-159">Ce type d’exception crée automatiquement un message qui comprend le chemin d’accès à la partie du JSON qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="06094-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="06094-160">Par exemple, l’instruction `throw new JsonException();` produit un message d’erreur comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="06094-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="06094-161">Si vous fournissez un message (par exemple, `throw new JsonException("Error occurred)`, l’exception fournit toujours le chemin d’accès dans la propriété <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="06094-161">If you do provide a message (for example, `throw new JsonException("Error occurred)`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="06094-162">Inscrire un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="06094-162">Register a custom converter</span></span>

<span data-ttu-id="06094-163">*Inscrire* un convertisseur personnalisé pour que les méthodes `Serialize` et `Deserialize` l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="06094-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="06094-164">Choisissez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="06094-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="06094-165">Ajoutez une instance de la classe de convertisseur à la collection <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06094-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="06094-166">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) aux propriétés qui requièrent le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="06094-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="06094-167">Appliquez l’attribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) à une classe ou un struct qui représente un type valeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="06094-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="06094-168">Exemple d’inscription-collection Converters</span><span class="sxs-lookup"><span data-stu-id="06094-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="06094-169">Voici un exemple qui rend le `ExampleDateTimeOffsetConverter` par défaut pour les propriétés de type `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="06094-169">Here's an example that makes the `ExampleDateTimeOffsetConverter` the default for properties of type `DateTimeOffset`:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="06094-170">Supposons que vous sérialisez le type suivant :</span><span class="sxs-lookup"><span data-stu-id="06094-170">Suppose you serialize the following type:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="06094-171">Voici un exemple de sortie JSON qui montre que le convertisseur personnalisé a été utilisé :</span><span class="sxs-lookup"><span data-stu-id="06094-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="06094-172">Le code suivant utilise la même approche pour désérialiser à l’aide du convertisseur de `DateTimeOffset` personnalisé :</span><span class="sxs-lookup"><span data-stu-id="06094-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="06094-173">Exemple d’inscription-[JsonConverter] sur une propriété</span><span class="sxs-lookup"><span data-stu-id="06094-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="06094-174">Le code suivant sélectionne un convertisseur personnalisé pour la propriété `Date` :</span><span class="sxs-lookup"><span data-stu-id="06094-174">The following code selects a custom converter for the `Date` property:</span></span>

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="06094-175">Le code pour sérialiser et désérialiser `WeatherForecastWithConverter` ne requiert pas l’utilisation de `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="06094-175">The code to serialize and deserialize `WeatherForecastWithConverter` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="06094-176">Exemple d’inscription-[JsonConverter] sur un type</span><span class="sxs-lookup"><span data-stu-id="06094-176">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="06094-177">Voici le code qui crée un struct et lui applique l’attribut `[JsonConverter]` :</span><span class="sxs-lookup"><span data-stu-id="06094-177">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

<span data-ttu-id="06094-178">Voici le convertisseur personnalisé pour le struct précédent :</span><span class="sxs-lookup"><span data-stu-id="06094-178">Here's the custom converter for the preceding struct:</span></span>

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

<span data-ttu-id="06094-179">L’attribut `[JsonConvert]` sur le struct inscrit le convertisseur personnalisé comme valeur par défaut pour les propriétés de type `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="06094-179">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="06094-180">Le convertisseur est utilisé automatiquement sur la propriété `TemperatureC` du type suivant lors de la sérialisation ou de la désérialisation de ce dernier :</span><span class="sxs-lookup"><span data-stu-id="06094-180">The converter is automatically used on the `TemperatureC` property of the following type when you serialize or deserialize it:</span></span>

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a><span data-ttu-id="06094-181">Priorité d’inscription du convertisseur</span><span class="sxs-lookup"><span data-stu-id="06094-181">Converter registration precedence</span></span>

<span data-ttu-id="06094-182">Lors de la sérialisation ou de la désérialisation, un convertisseur est choisi pour chaque élément JSON dans l’ordre suivant, de la priorité la plus élevée à la plus faible :</span><span class="sxs-lookup"><span data-stu-id="06094-182">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="06094-183">`[JsonConverter]` appliquée à une propriété.</span><span class="sxs-lookup"><span data-stu-id="06094-183">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="06094-184">Convertisseur ajouté à la collection `Converters`.</span><span class="sxs-lookup"><span data-stu-id="06094-184">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="06094-185">`[JsonConverter]` appliqué à un type valeur personnalisé ou POCO.</span><span class="sxs-lookup"><span data-stu-id="06094-185">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="06094-186">Si plusieurs convertisseurs personnalisés pour un type sont inscrits dans la collection `Converters`, le premier convertisseur qui retourne la valeur true pour `CanConvert` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="06094-186">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="06094-187">Un convertisseur intégré est choisi uniquement si aucun convertisseur personnalisé applicable n’est inscrit.</span><span class="sxs-lookup"><span data-stu-id="06094-187">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="06094-188">Exemples de convertisseurs pour les scénarios courants</span><span class="sxs-lookup"><span data-stu-id="06094-188">Converter samples for common scenarios</span></span>

<span data-ttu-id="06094-189">Les sections suivantes fournissent des exemples de convertisseurs qui traitent de certains scénarios courants que les fonctionnalités intégrées ne gèrent pas.</span><span class="sxs-lookup"><span data-stu-id="06094-189">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="06094-190">Désérialiser les types inférés en propriétés d’objet</span><span class="sxs-lookup"><span data-stu-id="06094-190">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="06094-191">Lors de la désérialisation vers une propriété de type `Object`, un objet `JsonElement` est créé.</span><span class="sxs-lookup"><span data-stu-id="06094-191">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="06094-192">Cela est dû au fait que le désérialiseur ne sait pas quel type CLR créer, et qu’il ne tente pas de deviner.</span><span class="sxs-lookup"><span data-stu-id="06094-192">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="06094-193">Par exemple, si une propriété JSON a la valeur « true », le désérialiseur ne déduit pas que la valeur est un `Boolean`, et si un élément a « 01/01/2019 », le désérialiseur ne déduit pas qu’il s’agit d’un `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="06094-193">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="06094-194">L’inférence de type peut être inexacte.</span><span class="sxs-lookup"><span data-stu-id="06094-194">Type inference can be inaccurate.</span></span> <span data-ttu-id="06094-195">Si le désérialiseur analyse un nombre JSON qui n’a pas de virgule décimale comme `long`, cela peut entraîner des problèmes hors limites si la valeur a été sérialisée à l’origine en tant que `ulong` ou `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="06094-195">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="06094-196">L’analyse d’un nombre qui a une virgule décimale comme `double` peut perdre la précision si le nombre a été initialement sérialisé en tant que `decimal`.</span><span class="sxs-lookup"><span data-stu-id="06094-196">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="06094-197">Pour les scénarios qui requièrent l’inférence de type, le code suivant montre un convertisseur personnalisé pour les propriétés de `Object`.</span><span class="sxs-lookup"><span data-stu-id="06094-197">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="06094-198">Le code convertit :</span><span class="sxs-lookup"><span data-stu-id="06094-198">The code converts:</span></span>

* <span data-ttu-id="06094-199">`true` et `false` à `Boolean`</span><span class="sxs-lookup"><span data-stu-id="06094-199">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="06094-200">Nombres à `long` ou `double`</span><span class="sxs-lookup"><span data-stu-id="06094-200">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="06094-201">Dates à `DateTime`</span><span class="sxs-lookup"><span data-stu-id="06094-201">Dates to `DateTime`</span></span>
* <span data-ttu-id="06094-202">Chaînes à `string`</span><span class="sxs-lookup"><span data-stu-id="06094-202">Strings to `string`</span></span>
* <span data-ttu-id="06094-203">Tout le reste à `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="06094-203">Everything else to `JsonElement`</span></span>

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

<span data-ttu-id="06094-204">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="06094-204">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

<span data-ttu-id="06094-205">Voici un exemple de type avec une propriété d’objet :</span><span class="sxs-lookup"><span data-stu-id="06094-205">Here's an example type with an Object property:</span></span>

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

<span data-ttu-id="06094-206">L’exemple suivant de JSON à désérialiser contient des valeurs qui seront désérialisées en tant que `DateTime`, `long`et `string`:</span><span class="sxs-lookup"><span data-stu-id="06094-206">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="06094-207">Sans le convertisseur personnalisé, la désérialisation place un `JsonElement` dans chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="06094-207">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="06094-208">Le [dossier tests unitaires](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) de l’espace de noms `System.Text.Json.Serialization` contient plus d’exemples de convertisseurs personnalisés qui gèrent la désérialisation vers les propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="06094-208">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="06094-209">Dictionnaire de prise en charge avec clé non-chaîne</span><span class="sxs-lookup"><span data-stu-id="06094-209">Support Dictionary with non-string key</span></span>

<span data-ttu-id="06094-210">La prise en charge intégrée pour les collections de dictionnaires concerne `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="06094-210">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="06094-211">Autrement dit, la clé doit être une chaîne.</span><span class="sxs-lookup"><span data-stu-id="06094-211">That is, the key must be a string.</span></span> <span data-ttu-id="06094-212">Pour prendre en charge un dictionnaire avec un entier ou un autre type en tant que clé, un convertisseur personnalisé est requis.</span><span class="sxs-lookup"><span data-stu-id="06094-212">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="06094-213">Le code suivant illustre un convertisseur personnalisé qui fonctionne avec `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="06094-213">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="06094-214">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="06094-214">The following code registers the converter:</span></span>

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

<span data-ttu-id="06094-215">Le convertisseur peut sérialiser et désérialiser la propriété `TemperatureRanges` de la classe suivante qui utilise le `Enum`suivant :</span><span class="sxs-lookup"><span data-stu-id="06094-215">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

<span data-ttu-id="06094-216">La sortie JSON de la sérialisation ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="06094-216">The JSON output from serialization looks like the following example:</span></span>

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="06094-217">Le [dossier tests unitaires](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) de l’espace de noms `System.Text.Json.Serialization` contient des exemples de convertisseurs personnalisés qui gèrent des dictionnaires non-clés.</span><span class="sxs-lookup"><span data-stu-id="06094-217">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="06094-218">Prendre en charge la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="06094-218">Support polymorphic deserialization</span></span>

<span data-ttu-id="06094-219">[La sérialisation polymorphe](system-text-json-how-to.md#serialize-properties-of-derived-classes) ne nécessite pas de convertisseur personnalisé, mais la désérialisation requiert un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="06094-219">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="06094-220">Supposons, par exemple, que vous avez une classe de base abstraite `Person`, avec `Employee` et `Customer` classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="06094-220">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="06094-221">La désérialisation polymorphe signifie qu’au moment du design vous pouvez spécifier `Person` comme cible de désérialisation, et les objets `Customer` et `Employee` dans le JSON sont correctement désérialisés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="06094-221">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="06094-222">Pendant la désérialisation, vous devez trouver des indices qui identifient le type requis dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="06094-222">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="06094-223">Les types d’indices disponibles varient en fonction de chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="06094-223">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="06094-224">Par exemple, une propriété de discriminateur peut être disponible ou vous devrez peut-être vous appuyer sur la présence ou l’absence d’une propriété particulière.</span><span class="sxs-lookup"><span data-stu-id="06094-224">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="06094-225">La version actuelle de `System.Text.Json` ne fournit pas d’attributs pour spécifier comment gérer les scénarios de désérialisation polymorphe, donc les convertisseurs personnalisés sont requis.</span><span class="sxs-lookup"><span data-stu-id="06094-225">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="06094-226">Le code suivant illustre une classe de base, deux classes dérivées et un convertisseur personnalisé pour eux.</span><span class="sxs-lookup"><span data-stu-id="06094-226">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="06094-227">Le convertisseur utilise une propriété de discriminateur pour effectuer une désérialisation polymorphe.</span><span class="sxs-lookup"><span data-stu-id="06094-227">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="06094-228">Le discriminateur de type ne figure pas dans les définitions de classe, mais il est créé au cours de la sérialisation et est lu pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="06094-228">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

<span data-ttu-id="06094-229">Le code suivant inscrit le convertisseur :</span><span class="sxs-lookup"><span data-stu-id="06094-229">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

<span data-ttu-id="06094-230">Le convertisseur peut désérialiser JSON qui a été créé à l’aide du même convertisseur pour sérialiser, par exemple :</span><span class="sxs-lookup"><span data-stu-id="06094-230">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="06094-231">Autres exemples de convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="06094-231">Other custom converter samples</span></span>

<span data-ttu-id="06094-232">Le [dossier tests unitaires](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) dans le code source `System.Text.Json.Serialization` comprend d’autres exemples de convertisseurs personnalisés, tels que :</span><span class="sxs-lookup"><span data-stu-id="06094-232">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="06094-233">convertisseur de `Int32` qui convertit la valeur null en valeur 0 lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="06094-233">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="06094-234">`Int32` convertisseur qui autorise les valeurs de chaîne et de nombre lors de la désérialisation</span><span class="sxs-lookup"><span data-stu-id="06094-234">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="06094-235">convertisseur de `Enum`</span><span class="sxs-lookup"><span data-stu-id="06094-235">`Enum` converter</span></span>
* <span data-ttu-id="06094-236">convertisseur de `List<T>` qui accepte les données externes</span><span class="sxs-lookup"><span data-stu-id="06094-236">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="06094-237">convertisseur de `Long[]` qui fonctionne avec une liste de nombres délimités par des virgules</span><span class="sxs-lookup"><span data-stu-id="06094-237">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="06094-238">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="06094-238">Additional resources</span></span>

* [<span data-ttu-id="06094-239">Vue d’ensemble de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="06094-239">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="06094-240">Informations de référence sur l’API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="06094-240">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="06094-241">Utilisation de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="06094-241">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="06094-242">Code source pour les convertisseurs intégrés</span><span class="sxs-lookup"><span data-stu-id="06094-242">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="06094-243">GitHub problèmes liés aux convertisseurs personnalisés pour `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="06094-243">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="06094-244">36639 présentation des convertisseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="06094-244">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="06094-245">38713 à propos de la désérialisation vers l’objet</span><span class="sxs-lookup"><span data-stu-id="06094-245">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="06094-246">40120 à propos des dictionnaires non-clés-chaîne</span><span class="sxs-lookup"><span data-stu-id="06094-246">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="06094-247">37787 à propos de la désérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="06094-247">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
