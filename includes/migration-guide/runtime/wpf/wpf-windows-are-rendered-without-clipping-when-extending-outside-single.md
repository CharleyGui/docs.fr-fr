---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497800"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="8221a-101">Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran</span><span class="sxs-lookup"><span data-stu-id="8221a-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="8221a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8221a-102">Details</span></span>

<span data-ttu-id="8221a-103">Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans.</span><span class="sxs-lookup"><span data-stu-id="8221a-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="8221a-104">Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.</span><span class="sxs-lookup"><span data-stu-id="8221a-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8221a-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8221a-105">Suggestion</span></span>

<span data-ttu-id="8221a-106">Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="8221a-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="8221a-107">Name</span><span class="sxs-lookup"><span data-stu-id="8221a-107">Name</span></span>    | <span data-ttu-id="8221a-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="8221a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8221a-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="8221a-109">Scope</span></span>   |<span data-ttu-id="8221a-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="8221a-110">Minor</span></span>|
|<span data-ttu-id="8221a-111">Version</span><span class="sxs-lookup"><span data-stu-id="8221a-111">Version</span></span>|<span data-ttu-id="8221a-112">4,6</span><span class="sxs-lookup"><span data-stu-id="8221a-112">4.6</span></span>|
|<span data-ttu-id="8221a-113">Type</span><span class="sxs-lookup"><span data-stu-id="8221a-113">Type</span></span>|<span data-ttu-id="8221a-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8221a-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8221a-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="8221a-115">Affected APIs</span></span>

<span data-ttu-id="8221a-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="8221a-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
