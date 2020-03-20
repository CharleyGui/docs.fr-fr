---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858650"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="f709b-101">Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran</span><span class="sxs-lookup"><span data-stu-id="f709b-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f709b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f709b-102">Details</span></span>|<span data-ttu-id="f709b-103">Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans.</span><span class="sxs-lookup"><span data-stu-id="f709b-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="f709b-104">Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.</span><span class="sxs-lookup"><span data-stu-id="f709b-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="f709b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f709b-105">Suggestion</span></span>|<span data-ttu-id="f709b-106">Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="f709b-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="f709b-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="f709b-107">Scope</span></span>|<span data-ttu-id="f709b-108">Secondaire</span><span class="sxs-lookup"><span data-stu-id="f709b-108">Minor</span></span>|
|<span data-ttu-id="f709b-109">Version</span><span class="sxs-lookup"><span data-stu-id="f709b-109">Version</span></span>|<span data-ttu-id="f709b-110">4.6</span><span class="sxs-lookup"><span data-stu-id="f709b-110">4.6</span></span>|
|<span data-ttu-id="f709b-111">Type</span><span class="sxs-lookup"><span data-stu-id="f709b-111">Type</span></span>|<span data-ttu-id="f709b-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="f709b-112">Runtime</span></span>|
