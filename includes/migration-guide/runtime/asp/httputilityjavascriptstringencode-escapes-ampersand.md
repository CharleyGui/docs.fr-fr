---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619925"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="d89bd-101">HttpUtility.JavaScriptStringEncode place le caractère esperluette (&) dans une séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="d89bd-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="d89bd-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d89bd-102">Details</span></span>

<span data-ttu-id="d89bd-103">Depuis .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> place le caractère esperluette (&amp;) dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="d89bd-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d89bd-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d89bd-104">Suggestion</span></span>

<span data-ttu-id="d89bd-105">Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d89bd-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="d89bd-106">Nom</span><span class="sxs-lookup"><span data-stu-id="d89bd-106">Name</span></span>    | <span data-ttu-id="d89bd-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="d89bd-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d89bd-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="d89bd-108">Scope</span></span>   |<span data-ttu-id="d89bd-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d89bd-109">Minor</span></span>|
|<span data-ttu-id="d89bd-110">Version</span><span class="sxs-lookup"><span data-stu-id="d89bd-110">Version</span></span>|<span data-ttu-id="d89bd-111">4,5</span><span class="sxs-lookup"><span data-stu-id="d89bd-111">4.5</span></span>|
|<span data-ttu-id="d89bd-112">Type</span><span class="sxs-lookup"><span data-stu-id="d89bd-112">Type</span></span>|<span data-ttu-id="d89bd-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="d89bd-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d89bd-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="d89bd-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
