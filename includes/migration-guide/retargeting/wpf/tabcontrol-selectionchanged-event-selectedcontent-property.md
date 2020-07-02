---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614606"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="5ccc2-101">Événement TabControl SelectionChanged et propriété SelectedContent</span><span class="sxs-lookup"><span data-stu-id="5ccc2-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="5ccc2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5ccc2-102">Details</span></span>

<span data-ttu-id="5ccc2-103">À compter de .NET Framework 4.7.1, un <xref:System.Windows.Controls.TabControl> met à jour la valeur de sa propriété <xref:System.Windows.Controls.TabControl.SelectedContent> avant de déclencher l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> quand sa sélection change. Dans .NET Framework 4.7 et antérieur, la mise à jour de SelectedContent se produisait après l’événement.</span><span class="sxs-lookup"><span data-stu-id="5ccc2-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5ccc2-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5ccc2-104">Suggestion</span></span>

<span data-ttu-id="5ccc2-105">Les applications qui ciblent .NET Framework 4.7.1 ou ultérieur peuvent refuser ce changement et utiliser le comportement hérité en ajoutant le code suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="5ccc2-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="5ccc2-106">Les applications qui ciblent .NET Framework 4.7 ou antérieur mais qui s’exécutent sur .NET Framework 4.7.1 ou ultérieur peuvent activer le nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier .configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="5ccc2-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="5ccc2-107">Nom</span><span class="sxs-lookup"><span data-stu-id="5ccc2-107">Name</span></span>    | <span data-ttu-id="5ccc2-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="5ccc2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5ccc2-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="5ccc2-109">Scope</span></span>   | <span data-ttu-id="5ccc2-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5ccc2-110">Minor</span></span>       |
| <span data-ttu-id="5ccc2-111">Version</span><span class="sxs-lookup"><span data-stu-id="5ccc2-111">Version</span></span> | <span data-ttu-id="5ccc2-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="5ccc2-112">4.7.1</span></span>       |
| <span data-ttu-id="5ccc2-113">Type</span><span class="sxs-lookup"><span data-stu-id="5ccc2-113">Type</span></span>    | <span data-ttu-id="5ccc2-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5ccc2-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5ccc2-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="5ccc2-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
