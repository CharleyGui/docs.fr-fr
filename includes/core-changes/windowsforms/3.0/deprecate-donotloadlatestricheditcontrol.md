---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937030"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="45719-101">DoNotLoadLatestRichEditControl commutateur de compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="45719-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="45719-102">Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="45719-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="45719-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="45719-103">Change description</span></span>

<span data-ttu-id="45719-104">Dans le cadre .NET 4.6.2 et <xref:System.Windows.Forms.RichTextBox> les versions précédentes, le contrôle instantanémentait le contrôle Win32 RichEdit v3.0, et <xref:System.Windows.Forms.RichTextBox> pour les applications qui ciblent .NET Framework 4.7.1, le contrôle serait instantanée RichEdit v4.1 (en *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="45719-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="45719-105">Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et les versions ultérieures de se retirer du nouveau contrôle RichEdit v4.1 et d’utiliser l’ancien contrôle RichEdit v3 à la place.</span><span class="sxs-lookup"><span data-stu-id="45719-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="45719-106">Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="45719-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="45719-107">Seules les nouvelles <xref:System.Windows.Forms.RichTextBox> versions du contrôle sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="45719-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45719-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="45719-108">Version introduced</span></span>

<span data-ttu-id="45719-109">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="45719-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45719-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="45719-110">Recommended action</span></span>

<span data-ttu-id="45719-111">Retirez l’interrupteur.</span><span class="sxs-lookup"><span data-stu-id="45719-111">Remove the switch.</span></span> <span data-ttu-id="45719-112">Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="45719-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="45719-113">Category</span><span class="sxs-lookup"><span data-stu-id="45719-113">Category</span></span>

<span data-ttu-id="45719-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45719-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45719-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="45719-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
