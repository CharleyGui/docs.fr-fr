---
title: 'Modification avec rupture : les applications ASP.NET Core autorisent la désérialisation des nombres entre guillemets'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où les applications de ASP.NET Core désérialiseront correctement les nombres représentés en tant que chaînes JSON au lieu de lever une exception.
ms.date: 10/21/2020
ms.openlocfilehash: fc8a4c6638be391c22c7cfb2fc7c216c88377f29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760908"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="f764d-103">Les applications ASP.NET Core autorisent la désérialisation des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="f764d-103">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="f764d-104">À compter de .NET 5,0, les applications ASP.NET Core utilisent les options de désérialisation par défaut comme spécifié par <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f764d-104">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f764d-105">L' <xref:System.Text.Json.JsonSerializerDefaults.Web> ensemble d’options comprend la définition de la valeur <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f764d-105">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f764d-106">Cette modification signifie que ASP.NET Core applications désérialiseront correctement les nombres représentés en tant que chaînes JSON au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="f764d-106">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings instead of throwing an exception.</span></span>

## <a name="change-description"></a><span data-ttu-id="f764d-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f764d-107">Change description</span></span>

<span data-ttu-id="f764d-108">Dans .NET Core 3,0-3,1, <xref:System.Text.Json.JsonSerializer> lève une lors de la <xref:System.Text.Json.JsonException> désérialisation s’il rencontre un nombre entre guillemets dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="f764d-108">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="f764d-109">Les nombres entre guillemets sont utilisés pour mapper les propriétés de nombre dans les graphiques d’objets.</span><span class="sxs-lookup"><span data-stu-id="f764d-109">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="f764d-110">Dans .NET Core 3,0-3,1, les nombres sont uniquement lus à partir de <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> jetons.</span><span class="sxs-lookup"><span data-stu-id="f764d-110">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="f764d-111">À compter de .NET 5,0, les nombres entre guillemets dans les charges utiles JSON sont considérés comme valides, par défaut, pour les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f764d-111">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="f764d-112">Aucune exception n’est levée pendant la désérialisation des nombres entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="f764d-112">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="f764d-113">Il n’y a aucun changement de comportement pour la valeur par défaut, autonome <xref:System.Text.Json.JsonSerializer> ou <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="f764d-113">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="f764d-114">Il ne s’agit techniquement pas d’une modification avec rupture, car cela rend un scénario plus permissif au lieu de plus restrictif (autrement dit, il parvient à forcer un nombre à partir d’une chaîne JSON au lieu de lever une exception).</span><span class="sxs-lookup"><span data-stu-id="f764d-114">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="f764d-115">Toutefois, étant donné qu’il s’agit d’un changement de comportement significatif qui affecte de nombreuses applications ASP.NET Core, il est documenté ici.</span><span class="sxs-lookup"><span data-stu-id="f764d-115">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="f764d-116">Les <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> méthodes d’extension et utilisent également le <xref:System.Text.Json.JsonSerializerDefaults.Web> jeu d’options de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f764d-116">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f764d-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f764d-117">Version introduced</span></span>

<span data-ttu-id="f764d-118">5.0</span><span class="sxs-lookup"><span data-stu-id="f764d-118">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f764d-119">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f764d-119">Reason for change</span></span>

<span data-ttu-id="f764d-120">Plusieurs utilisateurs ont demandé une option pour la gestion des nombres plus permissif dans <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f764d-120">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="f764d-121">Ce feedback indique que de nombreux producteurs JSON (par exemple, les services sur le Web) émettent des chiffres entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="f764d-121">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="f764d-122">En autorisant la lecture des nombres entre guillemets (désérialisés), les applications .NET peuvent analyser ces charges utiles, par défaut, dans les contextes Web.</span><span class="sxs-lookup"><span data-stu-id="f764d-122">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="f764d-123">La configuration est exposée par le biais de <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> afin que vous puissiez spécifier les mêmes options sur différentes couches d’application, par exemple, client, serveur et partagé.</span><span class="sxs-lookup"><span data-stu-id="f764d-123">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f764d-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f764d-124">Recommended action</span></span>

<span data-ttu-id="f764d-125">Si cette modification est perturbatrice, par exemple, si vous dépendez de la gestion des nombres stricts pour la validation, vous pouvez réactiver le comportement précédent.</span><span class="sxs-lookup"><span data-stu-id="f764d-125">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="f764d-126">Affectez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> à l’option la valeur <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f764d-126">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f764d-127">Pour les applications ASP.NET Core MVC et API Web, vous pouvez configurer l’option dans à `Startup` l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="f764d-127">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a><span data-ttu-id="f764d-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="f764d-128">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
