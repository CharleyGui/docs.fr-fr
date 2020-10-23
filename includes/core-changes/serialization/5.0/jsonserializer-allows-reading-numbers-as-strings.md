---
ms.openlocfilehash: a93856aac97af5c392a2e4698d2da42413cfc3c8
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434988"
---
### <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="01aab-101">Les applications ASP.NET Core autorisent la désérialisation des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="01aab-101">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="01aab-102">À compter de .NET 5,0, les applications ASP.NET Core utilisent les options de désérialisation par défaut comme spécifié par <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="01aab-102">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01aab-103">L' <xref:System.Text.Json.JsonSerializerDefaults.Web> ensemble d’options comprend la définition de la valeur <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="01aab-103">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01aab-104">Cette modification signifie que ASP.NET Core applications désérialiseront correctement les nombres représentés en tant que chaînes JSON, au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="01aab-104">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings, instead of throwing an exception.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01aab-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="01aab-105">Change description</span></span>

<span data-ttu-id="01aab-106">Dans .NET Core 3,0-3,1, <xref:System.Text.Json.JsonSerializer> lève une lors de la <xref:System.Text.Json.JsonException> désérialisation s’il rencontre un nombre entre guillemets dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="01aab-106">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="01aab-107">Les nombres entre guillemets sont utilisés pour mapper les propriétés de nombre dans les graphiques d’objets.</span><span class="sxs-lookup"><span data-stu-id="01aab-107">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="01aab-108">Dans .NET Core 3,0-3,1, les nombres sont uniquement lus à partir de <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> jetons.</span><span class="sxs-lookup"><span data-stu-id="01aab-108">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="01aab-109">À compter de .NET 5,0, les nombres entre guillemets dans les charges utiles JSON sont considérés comme valides, par défaut, pour les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="01aab-109">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="01aab-110">Aucune exception n’est levée pendant la désérialisation des nombres entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="01aab-110">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="01aab-111">Il n’y a aucun changement de comportement pour la valeur par défaut, autonome <xref:System.Text.Json.JsonSerializer> ou <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="01aab-111">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="01aab-112">Il ne s’agit techniquement pas d’une modification avec rupture, car cela rend un scénario plus permissif au lieu de plus restrictif (autrement dit, il parvient à forcer un nombre à partir d’une chaîne JSON au lieu de lever une exception).</span><span class="sxs-lookup"><span data-stu-id="01aab-112">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="01aab-113">Toutefois, étant donné qu’il s’agit d’un changement de comportement significatif qui affecte de nombreuses applications ASP.NET Core, il est documenté ici.</span><span class="sxs-lookup"><span data-stu-id="01aab-113">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="01aab-114">Les <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> méthodes d’extension et utilisent également le <xref:System.Text.Json.JsonSerializerDefaults.Web> jeu d’options de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="01aab-114">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01aab-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="01aab-115">Version introduced</span></span>

<span data-ttu-id="01aab-116">5.0</span><span class="sxs-lookup"><span data-stu-id="01aab-116">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01aab-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="01aab-117">Reason for change</span></span>

<span data-ttu-id="01aab-118">Plusieurs utilisateurs ont demandé une option pour la gestion des nombres plus permissif dans <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="01aab-118">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="01aab-119">Ce feedback indique que de nombreux producteurs JSON (par exemple, les services sur le Web) émettent des chiffres entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="01aab-119">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="01aab-120">En autorisant la lecture des nombres entre guillemets (désérialisés), les applications .NET peuvent analyser ces charges utiles, par défaut, dans les contextes Web.</span><span class="sxs-lookup"><span data-stu-id="01aab-120">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="01aab-121">La configuration est exposée par le biais de <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> afin que vous puissiez spécifier les mêmes options sur différentes couches d’application, par exemple, client, serveur et partagé.</span><span class="sxs-lookup"><span data-stu-id="01aab-121">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01aab-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="01aab-122">Recommended action</span></span>

<span data-ttu-id="01aab-123">Si cette modification est perturbatrice, par exemple, si vous dépendez de la gestion des nombres stricts pour la validation, vous pouvez réactiver le comportement précédent.</span><span class="sxs-lookup"><span data-stu-id="01aab-123">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="01aab-124">Affectez <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> à l’option la valeur <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="01aab-124">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="01aab-125">Pour les applications ASP.NET Core MVC et API Web, vous pouvez configurer l’option dans à `Startup` l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="01aab-125">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

#### <a name="category"></a><span data-ttu-id="01aab-126">Category</span><span class="sxs-lookup"><span data-stu-id="01aab-126">Category</span></span>

- <span data-ttu-id="01aab-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="01aab-127">ASP.NET Core</span></span>
- <span data-ttu-id="01aab-128">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="01aab-128">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01aab-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="01aab-129">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
