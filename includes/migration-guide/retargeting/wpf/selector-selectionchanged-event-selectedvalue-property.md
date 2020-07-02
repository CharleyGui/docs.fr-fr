---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614598"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="418b8-101">Événement SelectionChanged et propriété SelectedValue de Selector</span><span class="sxs-lookup"><span data-stu-id="418b8-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="418b8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="418b8-102">Details</span></span>

<span data-ttu-id="418b8-103">À compter de .NET Framework 4.7.1, un <xref:System.Windows.Controls.Primitives.Selector> met toujours à jour la valeur de sa propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> avant de déclencher l’événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> quand sa sélection change.</span><span class="sxs-lookup"><span data-stu-id="418b8-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="418b8-104">La propriété SelectedValue est ainsi cohérente avec les autres propriétés de sélection (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> et <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), qui sont mises à jour avant le déclenchement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="418b8-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="418b8-105">Dans .NET Framework 4.7 et antérieur, la mise à jour de SelectedValue avait lieu avant l’événement dans la plupart des cas, mais elle se produisait après l’événement si le changement de sélection résultait du changement de la propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="418b8-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="418b8-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="418b8-106">Suggestion</span></span>

<span data-ttu-id="418b8-107">Les applications qui ciblent .NET Framework 4.7.1 ou ultérieur peuvent refuser ce changement et utiliser le comportement hérité en ajoutant le code suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="418b8-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="418b8-108">Les applications qui ciblent .NET Framework 4.7 ou antérieur mais qui s’exécutent sur .NET Framework 4.7.1 ou ultérieur peuvent activer le nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier .configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="418b8-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="418b8-109">Nom</span><span class="sxs-lookup"><span data-stu-id="418b8-109">Name</span></span>    | <span data-ttu-id="418b8-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="418b8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="418b8-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="418b8-111">Scope</span></span>   | <span data-ttu-id="418b8-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="418b8-112">Minor</span></span>       |
| <span data-ttu-id="418b8-113">Version</span><span class="sxs-lookup"><span data-stu-id="418b8-113">Version</span></span> | <span data-ttu-id="418b8-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="418b8-114">4.7.1</span></span>       |
| <span data-ttu-id="418b8-115">Type</span><span class="sxs-lookup"><span data-stu-id="418b8-115">Type</span></span>    | <span data-ttu-id="418b8-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="418b8-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="418b8-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="418b8-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
