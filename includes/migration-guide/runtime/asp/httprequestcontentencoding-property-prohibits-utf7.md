---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619919"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="2ac11-101">La propriété HttpRequest.ContentEncoding interdit UTF7</span><span class="sxs-lookup"><span data-stu-id="2ac11-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="2ac11-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2ac11-102">Details</span></span>

<span data-ttu-id="2ac11-103">À compter de .NET Framework 4.5, l’encodage UTF-7 est interdit dans le corps des <xref:System.Web.HttpRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2ac11-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="2ac11-104">Les données des applications qui dépendent des données UTF-7 entrantes ne seront pas décodées correctement dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="2ac11-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2ac11-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2ac11-105">Suggestion</span></span>

<span data-ttu-id="2ac11-106">Dans l’idéal, les applications doivent être mises à jour pour ne pas utiliser l’encodage UTF-7 dans les <xref:System.Web.HttpRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2ac11-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="2ac11-107">Vous pouvez aussi restaurer le comportement hérité à l’aide de l’attribut <code>aspnet:AllowUtf7RequestContentEncoding</code> de l’élément [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2ac11-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="2ac11-108">Nom</span><span class="sxs-lookup"><span data-stu-id="2ac11-108">Name</span></span>    | <span data-ttu-id="2ac11-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="2ac11-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2ac11-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="2ac11-110">Scope</span></span>   |<span data-ttu-id="2ac11-111">Edge</span><span class="sxs-lookup"><span data-stu-id="2ac11-111">Edge</span></span>|
|<span data-ttu-id="2ac11-112">Version</span><span class="sxs-lookup"><span data-stu-id="2ac11-112">Version</span></span>|<span data-ttu-id="2ac11-113">4,5</span><span class="sxs-lookup"><span data-stu-id="2ac11-113">4.5</span></span>|
|<span data-ttu-id="2ac11-114">Type</span><span class="sxs-lookup"><span data-stu-id="2ac11-114">Type</span></span>|<span data-ttu-id="2ac11-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="2ac11-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ac11-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="2ac11-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
