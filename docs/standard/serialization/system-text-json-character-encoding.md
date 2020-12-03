---
title: Comment personnaliser l’encodage de caractères avec System.Text.Json
description: Découvrez comment personnaliser l’encodage de caractères lors de la sérialisation et de la désérialisation de JSON dans .NET.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: f6a50a3ca2a5e871294cf7c056cbf197a61cd668
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439995"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="1f899-103">Comment personnaliser l’encodage de caractères avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="1f899-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="1f899-104">Par défaut, le sérialiseur échappe tous les caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="1f899-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="1f899-105">Autrement dit, il les remplace par `\uxxxx` où `xxxx` est le code Unicode du caractère.</span><span class="sxs-lookup"><span data-stu-id="1f899-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="1f899-106">Par exemple, si la `Summary` propriété dans le JSON suivant est définie sur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="1f899-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="1f899-107">Sérialiser les jeux de caractères de la langue</span><span class="sxs-lookup"><span data-stu-id="1f899-107">Serialize language character sets</span></span>

<span data-ttu-id="1f899-108">Pour sérialiser le ou les jeux de caractères d’une ou plusieurs langues sans échappement, spécifiez la ou les [plages Unicode](xref:System.Text.Unicode.UnicodeRanges) lors de la création d’une instance de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1f899-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="1f899-109">Ce code n’échappe pas aux caractères cyrilliques ou grecs.</span><span class="sxs-lookup"><span data-stu-id="1f899-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="1f899-110">Si la `Summary` propriété a la valeur cyrillique `жарко` , l' `WeatherForecast` objet est sérialisé comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1f899-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="1f899-111">Pour sérialiser tous les jeux de langues sans échappement, utilisez <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1f899-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="1f899-112">Sérialiser des caractères spécifiques</span><span class="sxs-lookup"><span data-stu-id="1f899-112">Serialize specific characters</span></span>

<span data-ttu-id="1f899-113">Une alternative consiste à spécifier des caractères individuels que vous souhaitez autoriser sans être échappés.</span><span class="sxs-lookup"><span data-stu-id="1f899-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="1f899-114">L’exemple suivant sérialise uniquement les deux premiers caractères de `жарко` :</span><span class="sxs-lookup"><span data-stu-id="1f899-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="1f899-115">Voici un exemple de JSON généré par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="1f899-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="1f899-116">Sérialiser tous les caractères</span><span class="sxs-lookup"><span data-stu-id="1f899-116">Serialize all characters</span></span>

<span data-ttu-id="1f899-117">Pour réduire l’échappement, vous pouvez utiliser <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1f899-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="1f899-118">Par rapport à l’encodeur par défaut, l' `UnsafeRelaxedJsonEscaping` encodeur est plus permissif en ce qui concerne la transmission sans séquence d’échappement des caractères :</span><span class="sxs-lookup"><span data-stu-id="1f899-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="1f899-119">Elle n’échappe pas les caractères HTML, tels que `<` ,, `>` `&` et `'` .</span><span class="sxs-lookup"><span data-stu-id="1f899-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="1f899-120">Il n’offre aucune protection supplémentaire en profondeur contre les attaques XSS ou de divulgation d’informations, telles que celles qui peuvent résulter du client et du serveur qui ne sont pas en accord avec le *jeu* de caractères.</span><span class="sxs-lookup"><span data-stu-id="1f899-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="1f899-121">Utilisez l’encodeur non sécurisé uniquement lorsqu’il est connu que le client interprétera la charge utile obtenue en tant que code JSON encodé UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1f899-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="1f899-122">Par exemple, vous pouvez l’utiliser si le serveur envoie l’en-tête de réponse `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="1f899-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="1f899-123">N’autorisez jamais l' `UnsafeRelaxedJsonEscaping` émission de la sortie brute dans une page HTML ou un `<script>` élément.</span><span class="sxs-lookup"><span data-stu-id="1f899-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f899-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f899-124">See also</span></span>

* [<span data-ttu-id="1f899-125">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="1f899-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="1f899-126">Comment écrire des sérialiseurs et des désérialiseurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="1f899-126">How to write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="1f899-127">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="1f899-127">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="1f899-128">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="1f899-128">[System.Text.Json API reference](xref:System.Text.Json)</span></span>