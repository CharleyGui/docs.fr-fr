---
title: Comment personnaliser l’encodage de caractères avec System.Text.Json
description: Découvrez comment personnaliser l’encodage de caractères lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 136a75ab73767fd79f99caa1d1387706ab655473
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215977"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="886d3-103">Comment personnaliser l’encodage de caractères avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="886d3-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="886d3-104">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="886d3-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="886d3-105">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="886d3-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="886d3-106">Par exemple, si la `Summary` propriété dans le JSON suivant est définie sur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="886d3-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="886d3-107">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="886d3-107">Serialize language character sets</span></span>

<span data-ttu-id="886d3-108">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="886d3-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="886d3-109">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="886d3-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="886d3-110">Si la `Summary` propriété a la valeur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="886d3-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="886d3-111">Par défaut, l’encodeur est initialisé avec la <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> plage.</span><span class="sxs-lookup"><span data-stu-id="886d3-111">By default, the encoder is initialized with the <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> range.</span></span>

<span data-ttu-id="886d3-112">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="886d3-112">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="886d3-113">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="886d3-113">Serialize specific characters</span></span>

<span data-ttu-id="886d3-114">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="886d3-114">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="886d3-115">L’exemple suivant sérialise uniquement les deux premiers caractères de `жарко` :</span><span class="sxs-lookup"><span data-stu-id="886d3-115">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="886d3-116">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="886d3-116">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a><span data-ttu-id="886d3-117">Listes de blocage</span><span class="sxs-lookup"><span data-stu-id="886d3-117">Block lists</span></span>

<span data-ttu-id="886d3-118">Les sections précédentes montrent comment spécifier des listes d’autorisation de points de code ou de plages que vous ne souhaitez pas placer dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="886d3-118">The preceding sections show how to specify allow lists of code points or ranges that you don't want to be escaped.</span></span> <span data-ttu-id="886d3-119">Toutefois, il existe des listes de blocage globales et spécifiques à l’encodeur qui peuvent remplacer certains points de code dans votre liste verte.</span><span class="sxs-lookup"><span data-stu-id="886d3-119">However, there are global and encoder-specific block lists that can override certain code points in your allow list.</span></span> <span data-ttu-id="886d3-120">Les points de code d’une liste rouge sont toujours placés dans une séquence d’échappement, même s’ils sont inclus dans votre liste verte.</span><span class="sxs-lookup"><span data-stu-id="886d3-120">Code points in a block list are always escaped, even if they're included in your allow list.</span></span>

### <a name="global-block-list"></a><span data-ttu-id="886d3-121">Liste rouge globale</span><span class="sxs-lookup"><span data-stu-id="886d3-121">Global block list</span></span>

<span data-ttu-id="886d3-122">La liste rouge globale contient des éléments tels que les caractères à usage privé, les caractères de contrôle, les points de code non définis et certaines catégories Unicode, telles que la [catégorie Space_Separator](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), à l’exception de `U+0020 SPACE` .</span><span class="sxs-lookup"><span data-stu-id="886d3-122">The global block list includes things like private-use characters, control characters, undefined code points, and certain Unicode categories, such as the [Space_Separator category](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), excluding `U+0020 SPACE`.</span></span> <span data-ttu-id="886d3-123">Par exemple, `U+3000 IDEOGRAPHIC SPACE` est placé dans une séquence d’échappement même si vous spécifiez la plage Unicode des [symboles CJC et des signes de ponctuation (u +3000-u + 303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) comme liste verte.</span><span class="sxs-lookup"><span data-stu-id="886d3-123">For example, `U+3000 IDEOGRAPHIC SPACE` is escaped even if you specify Unicode range [CJK Symbols and Punctuation (U+3000-U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) as your allow list.</span></span>

<span data-ttu-id="886d3-124">La liste rouge globale est un détail d’implémentation qui a changé dans chaque version de .NET Core et dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="886d3-124">The global block list is an implementation detail that has changed in every release of .NET Core and in .NET 5.</span></span> <span data-ttu-id="886d3-125">N’effectuez pas de dépendance sur un caractère qui est membre (ou n’est pas membre de) la liste rouge globale.</span><span class="sxs-lookup"><span data-stu-id="886d3-125">Don't take a dependency on a character being a member of (or not being a member of) the global block list.</span></span>

### <a name="encoder-specific-block-lists"></a><span data-ttu-id="886d3-126">Listes de blocs spécifiques à l’encodeur</span><span class="sxs-lookup"><span data-stu-id="886d3-126">Encoder-specific block lists</span></span>

<span data-ttu-id="886d3-127">Les exemples de points de code bloqués spécifiques à l’encodeur incluent `'<'` et `'&'` pour l' [encodeur html](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` pour l' [encodeur JSON](xref:System.Text.Encodings.Web.JavaScriptEncoder)et `'%'` pour l' [encodeur d’URL](xref:System.Text.Encodings.Web.UrlEncoder).</span><span class="sxs-lookup"><span data-stu-id="886d3-127">Examples of encoder-specific blocked code points include `'<'` and `'&'` for the [HTML encoder](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` for the [JSON encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder), and `'%'` for the [URL encoder](xref:System.Text.Encodings.Web.UrlEncoder).</span></span> <span data-ttu-id="886d3-128">Par exemple, l’encodeur HTML échappe toujours à l’esperluette ( `'&'` ), même si l’esperluette est `BasicLatin` comprise dans la plage et que tous les encodeurs sont initialisés avec `BasicLatin` par défaut.</span><span class="sxs-lookup"><span data-stu-id="886d3-128">For example, the HTML encoder always escapes ampersands (`'&'`), even though the ampersand is in the `BasicLatin` range and all the encoders are initialized with `BasicLatin` by default.</span></span>

## <a name="serialize-all-characters"></a><span data-ttu-id="886d3-129">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="886d3-129">Serialize all characters</span></span>

<span data-ttu-id="886d3-130">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="886d3-130">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="886d3-131">Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="886d3-131">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="886d3-132">Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .</span><span class="sxs-lookup"><span data-stu-id="886d3-132">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="886d3-133">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu* de caractères.</span><span class="sxs-lookup"><span data-stu-id="886d3-133">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="886d3-134">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="886d3-134">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="886d3-135">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="886d3-135">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="886d3-136">N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.</span><span class="sxs-lookup"><span data-stu-id="886d3-136">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="886d3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="886d3-137">See also</span></span>

* [<span data-ttu-id="886d3-138">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="886d3-138">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="886d3-139">Guide pratique pour sérialiser et désérialiser JSON</span><span class="sxs-lookup"><span data-stu-id="886d3-139">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="886d3-140">Instancier des instances JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="886d3-140">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="886d3-141">Activer la correspondance non sensible à la casse</span><span class="sxs-lookup"><span data-stu-id="886d3-141">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="886d3-142">Personnaliser les noms et valeurs de propriété</span><span class="sxs-lookup"><span data-stu-id="886d3-142">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="886d3-143">Ignorer les propriétés</span><span class="sxs-lookup"><span data-stu-id="886d3-143">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="886d3-144">Autoriser JSON non valide</span><span class="sxs-lookup"><span data-stu-id="886d3-144">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="886d3-145">Gérer le JSON de dépassement</span><span class="sxs-lookup"><span data-stu-id="886d3-145">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="886d3-146">Préserver les références</span><span class="sxs-lookup"><span data-stu-id="886d3-146">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="886d3-147">Types immuables et accesseurs non publics</span><span class="sxs-lookup"><span data-stu-id="886d3-147">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="886d3-148">Sérialisation polymorphe</span><span class="sxs-lookup"><span data-stu-id="886d3-148">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="886d3-149">Migrer de Newtonsoft.Json vers System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="886d3-149">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="886d3-150">Écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="886d3-150">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="886d3-151">Écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="886d3-151">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="886d3-152">Prise en charge DateTime et DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="886d3-152">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="886d3-153">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="886d3-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="886d3-154">[System.Text.Json. Référence de l’API de sérialisation](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="886d3-154">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
