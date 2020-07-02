---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621359"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="b61da-101">Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran</span><span class="sxs-lookup"><span data-stu-id="b61da-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="b61da-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b61da-102">Details</span></span>

<span data-ttu-id="b61da-103">Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans.</span><span class="sxs-lookup"><span data-stu-id="b61da-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="b61da-104">Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.</span><span class="sxs-lookup"><span data-stu-id="b61da-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b61da-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b61da-105">Suggestion</span></span>

<span data-ttu-id="b61da-106">Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="b61da-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="b61da-107">Nom</span><span class="sxs-lookup"><span data-stu-id="b61da-107">Name</span></span>    | <span data-ttu-id="b61da-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="b61da-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b61da-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="b61da-109">Scope</span></span>   |<span data-ttu-id="b61da-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="b61da-110">Minor</span></span>|
|<span data-ttu-id="b61da-111">Version</span><span class="sxs-lookup"><span data-stu-id="b61da-111">Version</span></span>|<span data-ttu-id="b61da-112">4.6</span><span class="sxs-lookup"><span data-stu-id="b61da-112">4.6</span></span>|
|<span data-ttu-id="b61da-113">Type</span><span class="sxs-lookup"><span data-stu-id="b61da-113">Type</span></span>|<span data-ttu-id="b61da-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="b61da-114">Runtime</span></span>|
