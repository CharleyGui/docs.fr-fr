---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606810"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="ce15a-101">Les actions upbutton et downbutton Domain de WinForm sont désormais synchronisées</span><span class="sxs-lookup"><span data-stu-id="ce15a-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="ce15a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ce15a-102">Details</span></span>

<span data-ttu-id="ce15a-103">Dans .NET Framework 4.7.1 et versions antérieures, l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> du contrôle <xref:System.Windows.Forms.DomainUpDown> est ignorée quand le texte du contrôle est présent, obligeant le développeur à utiliser l’action <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> sur le contrôle avant d’utiliser l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ce15a-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="ce15a-104">À compter de .NET Framework 4.7.2, les actions <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> et <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> fonctionnent indépendamment dans ce scénario et restent synchronisées.</span><span class="sxs-lookup"><span data-stu-id="ce15a-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ce15a-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ce15a-105">Suggestion</span></span>

<span data-ttu-id="ce15a-106">Une application doit s’exécuter sur .NET Framework 4.7.2 ou ultérieur pour tirer parti de ces changements.</span><span class="sxs-lookup"><span data-stu-id="ce15a-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="ce15a-107">Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce15a-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="ce15a-108">Recompilez-la pour qu’elle cible .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="ce15a-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="ce15a-109">Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ce15a-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="ce15a-110">Refusez le comportement de défilement hérité en ajoutant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ce15a-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ce15a-111">Name</span><span class="sxs-lookup"><span data-stu-id="ce15a-111">Name</span></span>    | <span data-ttu-id="ce15a-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="ce15a-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ce15a-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="ce15a-113">Scope</span></span>   | <span data-ttu-id="ce15a-114">Edge</span><span class="sxs-lookup"><span data-stu-id="ce15a-114">Edge</span></span>        |
| <span data-ttu-id="ce15a-115">Version</span><span class="sxs-lookup"><span data-stu-id="ce15a-115">Version</span></span> | <span data-ttu-id="ce15a-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="ce15a-116">4.7.2</span></span>       |
| <span data-ttu-id="ce15a-117">Type</span><span class="sxs-lookup"><span data-stu-id="ce15a-117">Type</span></span>    | <span data-ttu-id="ce15a-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ce15a-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ce15a-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="ce15a-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
