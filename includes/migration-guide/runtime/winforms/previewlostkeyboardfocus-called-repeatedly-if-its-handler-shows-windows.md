---
ms.openlocfilehash: c4a3d903894027a01d32ca132d1233da9d9c3ee5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497614"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="fd374-101">PreviewLostKeyboardFocus est appelé de façon répétée si son gestionnaire affiche une boîte de message Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd374-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="fd374-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fd374-102">Details</span></span>

<span data-ttu-id="fd374-103">À compter de la version 4.5 du .NET Framework, quand vous appelez <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> à partir d’un gestionnaire <xref:System.Windows.UIElement.PreviewLostKeyboardFocus>, le gestionnaire est redéclenché quand la boîte de message est fermée, ce qui peut aboutir à une boucle infinie de boîtes de message.</span><span class="sxs-lookup"><span data-stu-id="fd374-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fd374-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fd374-104">Suggestion</span></span>

<span data-ttu-id="fd374-105">Il existe deux options pour contourner ce problème :</span><span class="sxs-lookup"><span data-stu-id="fd374-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="fd374-106">Vous pouvez appeler <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd374-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="fd374-107">Vous pouvez afficher la boîte de message à partir d’un gestionnaire d’événements <xref:System.Windows.UIElement.LostKeyboardFocus> (au lieu du gestionnaire d’événements <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="fd374-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="fd374-108">Name</span><span class="sxs-lookup"><span data-stu-id="fd374-108">Name</span></span>    | <span data-ttu-id="fd374-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd374-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fd374-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="fd374-110">Scope</span></span>   |<span data-ttu-id="fd374-111">Edge</span><span class="sxs-lookup"><span data-stu-id="fd374-111">Edge</span></span>|
|<span data-ttu-id="fd374-112">Version</span><span class="sxs-lookup"><span data-stu-id="fd374-112">Version</span></span>|<span data-ttu-id="fd374-113">4,5</span><span class="sxs-lookup"><span data-stu-id="fd374-113">4.5</span></span>|
|<span data-ttu-id="fd374-114">Type</span><span class="sxs-lookup"><span data-stu-id="fd374-114">Type</span></span>|<span data-ttu-id="fd374-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="fd374-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fd374-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="fd374-116">Affected APIs</span></span>

- <xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.ContentElement.PreviewLostKeyboardFocus`
- `E:System.Windows.IInputElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement3D.PreviewLostKeyboardFocus`

-->
