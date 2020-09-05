---
ms.openlocfilehash: ed669364efe9dd8f57d831a3764dd3fc68cd5e05
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497017"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="04b39-101">La mauvaise gestion multipartite d’ASP.NET peut entraîner la perte de données de formulaire.</span><span class="sxs-lookup"><span data-stu-id="04b39-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="04b39-102">Détails</span><span class="sxs-lookup"><span data-stu-id="04b39-102">Details</span></span>

<span data-ttu-id="04b39-103">Dans les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, ASP.Net risque de mal analyser les valeurs limites multipartites, ce qui entraîne l’indisponibilité de données de formulaire pendant l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="04b39-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="04b39-104">Les applications qui ciblent .NET Framework 4.8 ou versions ultérieures analysent correctement les données multipartites pour que les valeurs de formulaire soient disponibles lors de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="04b39-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="04b39-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="04b39-105">Suggestion</span></span>

<span data-ttu-id="04b39-106">À compter des applications qui s’exécutent sur .NET Framework 4.8, quand vous ciblez .NET Framework 4.8 ou ultérieur à l’aide de l’élément <code>targetFrameworkVersion</code>, le comportement par défaut change pour supprimer les délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="04b39-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="04b39-107">Lorsque vous ciblez les versions précédentes du Framework ou que vous n’utilisez pas <code>targetFrameworkVersion</code>, les délimiteurs de fin de certaines valeurs sont toujours retournés. Ce comportement peut aussi être contrôlé explicitement avec un <code>appSetting</code> :</span><span class="sxs-lookup"><span data-stu-id="04b39-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="04b39-108">Name</span><span class="sxs-lookup"><span data-stu-id="04b39-108">Name</span></span>    | <span data-ttu-id="04b39-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="04b39-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="04b39-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="04b39-110">Scope</span></span>   |<span data-ttu-id="04b39-111">Unknown</span><span class="sxs-lookup"><span data-stu-id="04b39-111">Unknown</span></span>|
|<span data-ttu-id="04b39-112">Version</span><span class="sxs-lookup"><span data-stu-id="04b39-112">Version</span></span>|<span data-ttu-id="04b39-113">4.8</span><span class="sxs-lookup"><span data-stu-id="04b39-113">4.8</span></span>|
|<span data-ttu-id="04b39-114">Type</span><span class="sxs-lookup"><span data-stu-id="04b39-114">Type</span></span>|<span data-ttu-id="04b39-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="04b39-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="04b39-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="04b39-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
