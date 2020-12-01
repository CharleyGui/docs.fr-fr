---
title: Comment sérialiser des propriétés de classes dérivées avec System.Text.Json
description: Découvrez comment sérialiser des objets polymorphes lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b99a402ea4f4c664d3bfd75627ffaf94948d493
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439973"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-no-locsystemtextjson"></a><span data-ttu-id="4db66-103">Comment sérialiser des propriétés de classes dérivées avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4db66-103">How to serialize properties of derived classes with System.Text.Json</span></span>

<span data-ttu-id="4db66-104">Dans cet article, vous allez apprendre à sérialiser des propriétés de classes dérivées avec l' `System.Text.Json` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4db66-104">In this article, you will learn how to serialize properties of derived classes with the `System.Text.Json` namespace.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="4db66-105">Sérialiser les propriétés des classes dérivées</span><span class="sxs-lookup"><span data-stu-id="4db66-105">Serialize properties of derived classes</span></span>

<span data-ttu-id="4db66-106">La sérialisation d’une hiérarchie de type polymorphe n’est _pas_ prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4db66-106">Serialization of a polymorphic type hierarchy is _not_ supported.</span></span> <span data-ttu-id="4db66-107">Par exemple, si une propriété est définie comme une interface ou une classe abstraite, seules les propriétés définies sur l’interface ou la classe abstraite sont sérialisées, même si le type de runtime a des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="4db66-107">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="4db66-108">Les exceptions à ce comportement sont expliquées dans cette section.</span><span class="sxs-lookup"><span data-stu-id="4db66-108">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="4db66-109">Par exemple, supposons que vous avez une `WeatherForecast` classe et une classe dérivée `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="4db66-109">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::

<span data-ttu-id="4db66-110">Et supposons que l’argument de type de la `Serialize` méthode au moment de la compilation est `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="4db66-110">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::

<span data-ttu-id="4db66-111">Dans ce scénario, la `WindSpeed` propriété n’est pas sérialisée, même si l' `weatherForecast` objet est en fait un `WeatherForecastDerived` objet.</span><span class="sxs-lookup"><span data-stu-id="4db66-111">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="4db66-112">Seules les propriétés de la classe de base sont sérialisées :</span><span class="sxs-lookup"><span data-stu-id="4db66-112">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="4db66-113">Ce comportement est destiné à empêcher l’exposition accidentelle de données dans un type créé par le runtime dérivé.</span><span class="sxs-lookup"><span data-stu-id="4db66-113">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="4db66-114">Pour sérialiser les propriétés du type dérivé dans l’exemple précédent, utilisez l’une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="4db66-114">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="4db66-115">Appelez une surcharge de <xref:System.Text.Json.JsonSerializer.Serialize%2A> qui vous permet de spécifier le type au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="4db66-115">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::

* <span data-ttu-id="4db66-116">Déclarez l’objet à sérialiser en tant que `object` .</span><span class="sxs-lookup"><span data-stu-id="4db66-116">Declare the object to be serialized as `object`.</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::

<span data-ttu-id="4db66-117">Dans l’exemple de scénario précédent, les deux approches entraînent l’inclusion de la `WindSpeed` propriété dans la sortie JSON :</span><span class="sxs-lookup"><span data-stu-id="4db66-117">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="4db66-118">Ces approches fournissent la sérialisation polymorphe uniquement pour l’objet racine à sérialiser, et non pour les propriétés de cet objet racine.</span><span class="sxs-lookup"><span data-stu-id="4db66-118">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="4db66-119">Vous pouvez obtenir la sérialisation polymorphe pour les objets de niveau inférieur si vous les définissez en tant que type `object` .</span><span class="sxs-lookup"><span data-stu-id="4db66-119">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="4db66-120">Par exemple, supposons que votre `WeatherForecast` classe ait une propriété nommée `PreviousForecast` qui peut être définie en tant que type `WeatherForecast` ou `object` :</span><span class="sxs-lookup"><span data-stu-id="4db66-120">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::

<span data-ttu-id="4db66-121">Si la `PreviousForecast` propriété contient une instance de `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="4db66-121">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="4db66-122">La sortie JSON de la sérialisation `WeatherForecastWithPrevious` **n’inclut pas** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="4db66-122">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="4db66-123">La sortie JSON de la sérialisation `WeatherForecastWithPreviousAsObject` **comprend** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="4db66-123">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="4db66-124">Pour sérialiser `WeatherForecastWithPreviousAsObject` , il n’est pas nécessaire d’appeler `Serialize<object>` ou `GetType` parce que l’objet racine n’est pas celui d’un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="4db66-124">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="4db66-125">L’exemple de code suivant n’appelle pas `Serialize<object>` ou `GetType` :</span><span class="sxs-lookup"><span data-stu-id="4db66-125">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::

<span data-ttu-id="4db66-126">Le code précédent sérialise correctement `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="4db66-126">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="4db66-127">La même approche de la définition des propriétés `object` fonctionne avec les interfaces.</span><span class="sxs-lookup"><span data-stu-id="4db66-127">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="4db66-128">Supposons que vous disposez de l’interface et de l’implémentation suivantes, et que vous souhaitez sérialiser une classe avec des propriétés qui contiennent des instances d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="4db66-128">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::

<span data-ttu-id="4db66-129">Lorsque vous sérialisez une instance de `Forecasts` , `Tuesday` affiche uniquement la `WindSpeed` propriété, car `Tuesday` est défini comme `object` suit :</span><span class="sxs-lookup"><span data-stu-id="4db66-129">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::

<span data-ttu-id="4db66-130">L’exemple suivant montre le code JSON qui résulte du code précédent :</span><span class="sxs-lookup"><span data-stu-id="4db66-130">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="4db66-131">Pour plus d’informations sur **la sérialisation** polymorphe et sur la **désérialisation**, consultez [Comment migrer de Newtonsoft.Json vers System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="4db66-131">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="see-also"></a><span data-ttu-id="4db66-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4db66-132">See also</span></span>

* [<span data-ttu-id="4db66-133">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="4db66-133">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="4db66-134">Instancier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="4db66-134">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="4db66-135">Activer la correspondance qui ne respecte pas la casse</span><span class="sxs-lookup"><span data-stu-id="4db66-135">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="4db66-136">Personnaliser les noms et les valeurs des propriétés</span><span class="sxs-lookup"><span data-stu-id="4db66-136">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="4db66-137">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="4db66-137">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="4db66-138">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="4db66-138">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="4db66-139">Handle de dépassement JSON</span><span class="sxs-lookup"><span data-stu-id="4db66-139">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="4db66-140">Conserver les références circulaires</span><span class="sxs-lookup"><span data-stu-id="4db66-140">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="4db66-141">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="4db66-141">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* <span data-ttu-id="4db66-142">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="4db66-142">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
