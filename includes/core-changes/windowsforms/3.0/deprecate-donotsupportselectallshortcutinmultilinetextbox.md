---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556170"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="1929f-101">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="1929f-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="1929f-102">Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core et .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1929f-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1929f-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1929f-103">Change description</span></span>

<span data-ttu-id="1929f-104">À partir de .NET Framework 4.6.1, la sélection de la touche de raccourci <kbd>CTRL</kbd>  +  <kbd>a</kbd> dans un <xref:System.Windows.Forms.TextBox> contrôle sélectionne tout le texte.</span><span class="sxs-lookup"><span data-stu-id="1929f-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="1929f-105">Dans .NET Framework 4,6 et versions antérieures, la sélection de la touche de raccourci <kbd>CTRL</kbd>  +  <kbd>A</kbd> a échoué pour sélectionner tout le texte si les propriétés [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> sont toutes deux définies sur `true` .</span><span class="sxs-lookup"><span data-stu-id="1929f-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="1929f-106">Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité a été introduit dans .NET Framework 4.6.1 pour conserver le comportement d’origine.</span><span class="sxs-lookup"><span data-stu-id="1929f-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="1929f-107">Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1929f-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1929f-108">Dans .NET Core et .NET 5,0 et versions ultérieures, le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1929f-108">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1929f-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1929f-109">Version introduced</span></span>

<span data-ttu-id="1929f-110">3.0</span><span class="sxs-lookup"><span data-stu-id="1929f-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1929f-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1929f-111">Recommended action</span></span>

<span data-ttu-id="1929f-112">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="1929f-112">Remove the switch.</span></span> <span data-ttu-id="1929f-113">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="1929f-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1929f-114">Category</span><span class="sxs-lookup"><span data-stu-id="1929f-114">Category</span></span>

<span data-ttu-id="1929f-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1929f-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1929f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="1929f-116">Affected APIs</span></span>

- <span data-ttu-id="1929f-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="1929f-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
