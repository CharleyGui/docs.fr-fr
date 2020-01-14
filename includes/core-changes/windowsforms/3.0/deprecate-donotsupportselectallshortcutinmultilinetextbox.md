---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937044"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="2d6f8-101">Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge</span><span class="sxs-lookup"><span data-stu-id="2d6f8-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="2d6f8-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2d6f8-103">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="2d6f8-103">Change description</span></span>

<span data-ttu-id="2d6f8-104">À partir de .NET Framework 4.6.1, si vous sélectionnez la touche <kbd>Ctrl</kbd> + <kbd>une</kbd> touche de raccourci dans un contrôle <xref:System.Windows.Forms.TextBox> sélectionné tout le texte.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="2d6f8-105">Dans .NET Framework 4,6 et versions antérieures, le fait de sélectionner la touche <kbd>Ctrl</kbd> + <kbd>une</kbd> touche de raccourci n’a pas pu sélectionner tout le texte si les propriétés [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> ont toutes les deux la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="2d6f8-106">Le commutateur de compatibilité `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` a été introduit dans .NET Framework 4.6.1 pour conserver le comportement d’origine.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="2d6f8-107">Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2d6f8-108">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2d6f8-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2d6f8-109">Version introduced</span></span>

<span data-ttu-id="2d6f8-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="2d6f8-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2d6f8-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2d6f8-111">Recommended action</span></span>

<span data-ttu-id="2d6f8-112">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-112">Remove the switch.</span></span> <span data-ttu-id="2d6f8-113">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="2d6f8-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2d6f8-114">Catégorie</span><span class="sxs-lookup"><span data-stu-id="2d6f8-114">Category</span></span>

<span data-ttu-id="2d6f8-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d6f8-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2d6f8-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="2d6f8-116">Affected APIs</span></span>

- <span data-ttu-id="2d6f8-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="2d6f8-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
