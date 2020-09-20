---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770921"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="76adc-101">Changement du contraste élevé des contrôles ComboBox svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="76adc-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="76adc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="76adc-102">Details</span></span>

<span data-ttu-id="76adc-103">Dans l’[outil Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), les contrôles ComboBox n’étaient pas affichés dans la bonne couleur dans certains thèmes à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="76adc-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="76adc-104">Le problème a été résolu dans .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="76adc-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="76adc-105">Toutefois, en raison des besoins de compatibilité descendante des kits SDK du .NET Framework, le correctif n’était pas visible pour les clients par défaut.</span><span class="sxs-lookup"><span data-stu-id="76adc-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="76adc-106">.NET 4.8 fait apparaître ce changement en ajoutant les [commutateurs de configuration AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier svcTraceViewer.exe.config :</span><span class="sxs-lookup"><span data-stu-id="76adc-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a><span data-ttu-id="76adc-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="76adc-107">Suggestion</span></span>

<span data-ttu-id="76adc-108">Si vous ne souhaitez pas que le comportement du contraste élevé soit modifié, vous pouvez le désactiver en supprimant la section suivante du fichier svcTraceViewer.exe.config :</span><span class="sxs-lookup"><span data-stu-id="76adc-108">If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| <span data-ttu-id="76adc-109">Nom</span><span class="sxs-lookup"><span data-stu-id="76adc-109">Name</span></span>    | <span data-ttu-id="76adc-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="76adc-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="76adc-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="76adc-111">Scope</span></span>   | <span data-ttu-id="76adc-112">Edge</span><span class="sxs-lookup"><span data-stu-id="76adc-112">Edge</span></span>    |
| <span data-ttu-id="76adc-113">Version</span><span class="sxs-lookup"><span data-stu-id="76adc-113">Version</span></span> | <span data-ttu-id="76adc-114">4.8</span><span class="sxs-lookup"><span data-stu-id="76adc-114">4.8</span></span>     |
| <span data-ttu-id="76adc-115">Type</span><span class="sxs-lookup"><span data-stu-id="76adc-115">Type</span></span>    | <span data-ttu-id="76adc-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="76adc-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="76adc-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="76adc-117">Affected APIs</span></span>

<span data-ttu-id="76adc-118">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="76adc-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
