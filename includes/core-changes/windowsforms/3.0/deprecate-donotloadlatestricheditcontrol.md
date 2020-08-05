---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556165"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="cb7d8-101">Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge</span><span class="sxs-lookup"><span data-stu-id="cb7d8-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="cb7d8-102">Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core ou .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cb7d8-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="cb7d8-103">Change description</span></span>

<span data-ttu-id="cb7d8-104">Dans .NET Framework 4.6.2 et versions antérieures, le <xref:System.Windows.Forms.RichTextBox> contrôle instancie le contrôle Win32 RichEdit v 3.0 et, pour les applications qui ciblent .NET Framework 4.7.1, le <xref:System.Windows.Forms.RichTextBox> contrôle instancie RichEdit v 4.1 (dans *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="cb7d8-104">In .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control instantiates the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control instantiates RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="cb7d8-105">Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et versions ultérieures de refuser le nouveau contrôle RichEdit v 4.1 et d’utiliser à la place l’ancien contrôle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="cb7d8-106">Dans .NET Core et .NET 5,0 et versions ultérieures, le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-106">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="cb7d8-107">Seules les nouvelles versions du <xref:System.Windows.Forms.RichTextBox> contrôle sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-107">Only new versions of the <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cb7d8-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cb7d8-108">Version introduced</span></span>

<span data-ttu-id="cb7d8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="cb7d8-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cb7d8-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cb7d8-110">Recommended action</span></span>

<span data-ttu-id="cb7d8-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-111">Remove the switch.</span></span> <span data-ttu-id="cb7d8-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="cb7d8-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="cb7d8-113">Category</span><span class="sxs-lookup"><span data-stu-id="cb7d8-113">Category</span></span>

<span data-ttu-id="cb7d8-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb7d8-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cb7d8-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="cb7d8-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
