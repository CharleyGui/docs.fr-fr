---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496593"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a><span data-ttu-id="efd62-101">Le paramètre d’application « dataAnnotations:dataTypeAttribute:disableRegEx » est activé par défaut dans .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="efd62-101">"dataAnnotations:dataTypeAttribute:disableRegEx" app setting is on by default in .NET Framework 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="efd62-102">Détails</span><span class="sxs-lookup"><span data-stu-id="efd62-102">Details</span></span>

<span data-ttu-id="efd62-103">Dans .NET Framework 4.6.1, un paramètre d’application (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) a été introduit pour permettre aux utilisateurs de désactiver l’utilisation d’expressions régulières dans les attributs de type de données (tels que <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> et <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="efd62-103">In .NET Framework 4.6.1, an app setting (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) was introduced that allows users to disable the use of regular expressions in data type attributes (such as <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, and <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="efd62-104">Et ainsi de réduire les vulnérabilités de sécurité, comme empêcher la possibilité d’une attaque par déni de Service avec des expressions régulières spécifiques.</span><span class="sxs-lookup"><span data-stu-id="efd62-104">This helps to reduce security vulnerability such as avoiding the possibility of a Denial of Service attack using specific regular expressions.</span></span><br/><span data-ttu-id="efd62-105">Dans .NET Framework 4.6.1, ce paramètre d’application pour désactiver l’utilisation de RegEx a été défini sur <code>false</code> par défaut.</span><span class="sxs-lookup"><span data-stu-id="efd62-105">In .NET Framework 4.6.1, this app setting to disable RegEx usage was set to <code>false</code> by default.</span></span> <span data-ttu-id="efd62-106">À partir de .NET Framework 4.7.2, ce commutateur de configuration est défini sur <code>true</code> par défaut pour réduire encore davantage la vulnérabilité sécurisée pour les applications Web qui ciblent .NET Framework 4.7.2 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="efd62-106">Starting with .NET Framework 4.7.2, this config switch is set to <code>true</code> by default to further reduce secure vulnerability for web applications that target .NET Framework 4.7.2 and above.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="efd62-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="efd62-107">Suggestion</span></span>

<span data-ttu-id="efd62-108">Si vous trouvez que les expressions régulières de votre application web ne fonctionnent pas après la mise à niveau vers .NET Framework 4.7.2, vous pouvez mettre à jour la valeur du paramètre <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> sur <code>false</code> pour revenir au comportement précédent.</span><span class="sxs-lookup"><span data-stu-id="efd62-108">If you find that regular expressions in your web application do not work after upgrading to .NET Framework 4.7.2, you can update the value of the <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> setting to <code>false</code> to revert to the previous behavior.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="efd62-109">Name</span><span class="sxs-lookup"><span data-stu-id="efd62-109">Name</span></span>    | <span data-ttu-id="efd62-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="efd62-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="efd62-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="efd62-111">Scope</span></span>   |<span data-ttu-id="efd62-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="efd62-112">Minor</span></span>|
|<span data-ttu-id="efd62-113">Version</span><span class="sxs-lookup"><span data-stu-id="efd62-113">Version</span></span>|<span data-ttu-id="efd62-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="efd62-114">4.7.2</span></span>|
|<span data-ttu-id="efd62-115">Type</span><span class="sxs-lookup"><span data-stu-id="efd62-115">Type</span></span>|<span data-ttu-id="efd62-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="efd62-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="efd62-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="efd62-117">Affected APIs</span></span>

<span data-ttu-id="efd62-118">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="efd62-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
