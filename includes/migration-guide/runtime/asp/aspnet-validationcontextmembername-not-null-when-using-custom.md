---
ms.openlocfilehash: 904a6abee2b4b2cf2f5727fb70e286c8a1a592c4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496309"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="61951-101">ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé</span><span class="sxs-lookup"><span data-stu-id="61951-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="61951-102">Détails</span><span class="sxs-lookup"><span data-stu-id="61951-102">Details</span></span>

<span data-ttu-id="61951-103">Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="61951-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="61951-104">Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, elle retourne le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="61951-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="61951-105">À compter de [.NET Framework version préliminaire du correctif cumulatif pour .NET Framework 4,8 d’octobre 2019](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) , elle retourne `null` par défaut, mais vous pouvez choisir de retourner le nom du membre à la place.</span><span class="sxs-lookup"><span data-stu-id="61951-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="61951-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="61951-106">Suggestion</span></span>

<span data-ttu-id="61951-107">Ajoutez le paramètre suivant à votre fichier *web.config* pour que la propriété retourne le nom du membre dans [2019 .NET Framework version préliminaire du cumul de qualité](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4,8 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="61951-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="61951-108">Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, l’ajout de ce à votre fichier *web.config* restaure le comportement précédent et la propriété retourne `null` .</span><span class="sxs-lookup"><span data-stu-id="61951-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="61951-109">Name</span><span class="sxs-lookup"><span data-stu-id="61951-109">Name</span></span>    | <span data-ttu-id="61951-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="61951-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="61951-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="61951-111">Scope</span></span>   |<span data-ttu-id="61951-112">Unknown</span><span class="sxs-lookup"><span data-stu-id="61951-112">Unknown</span></span>|
|<span data-ttu-id="61951-113">Version</span><span class="sxs-lookup"><span data-stu-id="61951-113">Version</span></span>|<span data-ttu-id="61951-114">4.8</span><span class="sxs-lookup"><span data-stu-id="61951-114">4.8</span></span>|
|<span data-ttu-id="61951-115">Type</span><span class="sxs-lookup"><span data-stu-id="61951-115">Type</span></span>|<span data-ttu-id="61951-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="61951-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="61951-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="61951-117">Affected APIs</span></span>

- <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ComponentModel.DataAnnotations.ValidationContext.MemberName`

-->
