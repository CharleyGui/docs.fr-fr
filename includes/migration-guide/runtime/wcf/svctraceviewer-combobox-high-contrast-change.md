---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621989"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="14edc-101">Changement du contraste élevé des contrôles ComboBox svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="14edc-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="14edc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="14edc-102">Details</span></span>

<span data-ttu-id="14edc-103">Dans l’[outil Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), les contrôles ComboBox n’étaient pas affichés dans la bonne couleur dans certains thèmes à contraste élevé.</span><span class="sxs-lookup"><span data-stu-id="14edc-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="14edc-104">Le problème a été résolu dans .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="14edc-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="14edc-105">Toutefois, en raison des besoins de compatibilité descendante des kits SDK du .NET Framework, le correctif n’était pas visible pour les clients par défaut.</span><span class="sxs-lookup"><span data-stu-id="14edc-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="14edc-106">.NET 4.8 fait apparaître ce changement en ajoutant les [commutateurs de configuration AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier svcTraceViewer.exe.config :</span><span class="sxs-lookup"><span data-stu-id="14edc-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="14edc-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="14edc-107">Suggestion</span></span>

<ul><li><span data-ttu-id="14edc-108">Si vous ne voulez pas accepter ce changement de comportement du contraste élevé, vous pouvez le désactiver en supprimant la section suivante du fichier svcTraceViewer.exe.config :</span><span class="sxs-lookup"><span data-stu-id="14edc-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="14edc-109">Nom</span><span class="sxs-lookup"><span data-stu-id="14edc-109">Name</span></span>    | <span data-ttu-id="14edc-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="14edc-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="14edc-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="14edc-111">Scope</span></span>   |<span data-ttu-id="14edc-112">Edge</span><span class="sxs-lookup"><span data-stu-id="14edc-112">Edge</span></span>|
|<span data-ttu-id="14edc-113">Version</span><span class="sxs-lookup"><span data-stu-id="14edc-113">Version</span></span>|<span data-ttu-id="14edc-114">4.8</span><span class="sxs-lookup"><span data-stu-id="14edc-114">4.8</span></span>|
|<span data-ttu-id="14edc-115">Type</span><span class="sxs-lookup"><span data-stu-id="14edc-115">Type</span></span>|<span data-ttu-id="14edc-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="14edc-116">Runtime</span></span>|
