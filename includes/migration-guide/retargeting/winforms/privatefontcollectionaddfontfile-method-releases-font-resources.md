---
ms.openlocfilehash: 6ee290f6722480778381376f588e16877894f232
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606718"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="8056d-101">La méthode PrivateFontCollection.AddFontFile libère les ressources de police</span><span class="sxs-lookup"><span data-stu-id="8056d-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="8056d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8056d-102">Details</span></span>

<span data-ttu-id="8056d-103">Dans .NET Framework 4.7.1 et versions antérieures, une fois le <xref:System.Drawing.Text.PrivateFontCollection> supprimé pour les objets <xref:System.Drawing.Font>, la classe <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> ne libère pas les ressources de police GDI+ qui sont ajoutées à cette collection à l’aide de la méthode <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="8056d-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="8056d-104">Dans .NET Framework 4.7.2 et versions ultérieures, <xref:System.Drawing.Text.FontCollection.Dispose%2A> libère les polices GDI+ qui ont été ajoutées à la collection en tant que fichiers.</span><span class="sxs-lookup"><span data-stu-id="8056d-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8056d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8056d-105">Suggestion</span></span>

<span data-ttu-id="8056d-106">**Comment accepter ou refuser ces modifications** Pour qu’une application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.2 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8056d-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="8056d-107">Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="8056d-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="8056d-108">Recompilez-la pour qu’elle cible .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="8056d-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="8056d-109">Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="8056d-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="8056d-110">Faites-lui cibler .NET Framework version 4.7.1 ou antérieure et refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8056d-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="8056d-111">Si votre application cible .NET Framework 4.7.2 ou une version ultérieure et que vous souhaitez conserver le comportement hérité, choisissez de ne pas libérer les ressources de police en affectant explicitement à ce commutateur AppContext la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="8056d-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="8056d-112">Name</span><span class="sxs-lookup"><span data-stu-id="8056d-112">Name</span></span>    | <span data-ttu-id="8056d-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="8056d-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8056d-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="8056d-114">Scope</span></span>   | <span data-ttu-id="8056d-115">Edge</span><span class="sxs-lookup"><span data-stu-id="8056d-115">Edge</span></span>        |
| <span data-ttu-id="8056d-116">Version</span><span class="sxs-lookup"><span data-stu-id="8056d-116">Version</span></span> | <span data-ttu-id="8056d-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8056d-117">4.7.2</span></span>       |
| <span data-ttu-id="8056d-118">Type</span><span class="sxs-lookup"><span data-stu-id="8056d-118">Type</span></span>    | <span data-ttu-id="8056d-119">Reciblage</span><span class="sxs-lookup"><span data-stu-id="8056d-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8056d-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="8056d-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
