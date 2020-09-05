---
ms.openlocfilehash: 12fb72d5ee9fc0d6c57899589cb2b0da7db41f4a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496204"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="dc12c-101">HttpUtility.JavaScriptStringEncode place le caractère esperluette (&) dans une séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="dc12c-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="dc12c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="dc12c-102">Details</span></span>

<span data-ttu-id="dc12c-103">Depuis .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> place le caractère esperluette (&amp;) dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="dc12c-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dc12c-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="dc12c-104">Suggestion</span></span>

<span data-ttu-id="dc12c-105">Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="dc12c-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="dc12c-106">Name</span><span class="sxs-lookup"><span data-stu-id="dc12c-106">Name</span></span>    | <span data-ttu-id="dc12c-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="dc12c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dc12c-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="dc12c-108">Scope</span></span>   |<span data-ttu-id="dc12c-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="dc12c-109">Minor</span></span>|
|<span data-ttu-id="dc12c-110">Version</span><span class="sxs-lookup"><span data-stu-id="dc12c-110">Version</span></span>|<span data-ttu-id="dc12c-111">4,5</span><span class="sxs-lookup"><span data-stu-id="dc12c-111">4.5</span></span>|
|<span data-ttu-id="dc12c-112">Type</span><span class="sxs-lookup"><span data-stu-id="dc12c-112">Type</span></span>|<span data-ttu-id="dc12c-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="dc12c-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="dc12c-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="dc12c-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
