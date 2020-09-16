---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606851"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="4ba24-101">HttpUtility.JavaScriptStringEncode place le caractère esperluette (&) dans une séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="4ba24-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="4ba24-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4ba24-102">Details</span></span>

<span data-ttu-id="4ba24-103">Depuis .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> place le caractère esperluette (&amp;) dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="4ba24-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ba24-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4ba24-104">Suggestion</span></span>

<span data-ttu-id="4ba24-105">Si votre application dépend du comportement précédent de cette méthode, vous pouvez ajouter un paramètre aspnet:JavaScriptDoNotEncodeAmpersand à l’[élément appSettings ASP.NET](/previous-versions/aspnet/hh975440(v=vs.120)) dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4ba24-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="4ba24-106">Name</span><span class="sxs-lookup"><span data-stu-id="4ba24-106">Name</span></span>    | <span data-ttu-id="4ba24-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="4ba24-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ba24-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="4ba24-108">Scope</span></span>   |<span data-ttu-id="4ba24-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4ba24-109">Minor</span></span>|
|<span data-ttu-id="4ba24-110">Version</span><span class="sxs-lookup"><span data-stu-id="4ba24-110">Version</span></span>|<span data-ttu-id="4ba24-111">4.5</span><span class="sxs-lookup"><span data-stu-id="4ba24-111">4.5</span></span>|
|<span data-ttu-id="4ba24-112">Type</span><span class="sxs-lookup"><span data-stu-id="4ba24-112">Type</span></span>|<span data-ttu-id="4ba24-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="4ba24-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4ba24-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="4ba24-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
