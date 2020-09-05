---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496485"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="fd828-101">ObjectDisposedException levée par le vérificateur orthographique de WPF</span><span class="sxs-lookup"><span data-stu-id="fd828-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="fd828-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fd828-102">Details</span></span>

<span data-ttu-id="fd828-103">Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=fullName> levée par le vérificateur orthographique.</span><span class="sxs-lookup"><span data-stu-id="fd828-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="fd828-104">Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon.</span><span class="sxs-lookup"><span data-stu-id="fd828-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="fd828-105">Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="fd828-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fd828-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fd828-106">Suggestion</span></span>

<span data-ttu-id="fd828-107">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="fd828-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="fd828-108">Name</span><span class="sxs-lookup"><span data-stu-id="fd828-108">Name</span></span>    | <span data-ttu-id="fd828-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd828-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fd828-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="fd828-110">Scope</span></span>   |<span data-ttu-id="fd828-111">Edge</span><span class="sxs-lookup"><span data-stu-id="fd828-111">Edge</span></span>|
|<span data-ttu-id="fd828-112">Version</span><span class="sxs-lookup"><span data-stu-id="fd828-112">Version</span></span>|<span data-ttu-id="fd828-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="fd828-113">4.6.1</span></span>|
|<span data-ttu-id="fd828-114">Type</span><span class="sxs-lookup"><span data-stu-id="fd828-114">Type</span></span>|<span data-ttu-id="fd828-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="fd828-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fd828-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="fd828-116">Affected APIs</span></span>

<span data-ttu-id="fd828-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="fd828-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
