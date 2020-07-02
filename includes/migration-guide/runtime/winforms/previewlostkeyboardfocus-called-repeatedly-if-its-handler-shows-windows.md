---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620081"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="8b7fc-101">PreviewLostKeyboardFocus est appelé de façon répétée si son gestionnaire affiche une boîte de message Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b7fc-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="8b7fc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8b7fc-102">Details</span></span>

<span data-ttu-id="8b7fc-103">À compter de la version 4.5 du .NET Framework, quand vous appelez <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> à partir d’un gestionnaire <xref:System.Windows.UIElement.PreviewLostKeyboardFocus>, le gestionnaire est redéclenché quand la boîte de message est fermée, ce qui peut aboutir à une boucle infinie de boîtes de message.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8b7fc-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8b7fc-104">Suggestion</span></span>

<span data-ttu-id="8b7fc-105">Il existe deux options pour contourner ce problème :</span><span class="sxs-lookup"><span data-stu-id="8b7fc-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="8b7fc-106">Vous pouvez appeler <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> au lieu de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="8b7fc-107">Vous pouvez afficher la boîte de message à partir d’un gestionnaire d’événements <xref:System.Windows.UIElement.LostKeyboardFocus> (au lieu du gestionnaire d’événements <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="8b7fc-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="8b7fc-108">Nom</span><span class="sxs-lookup"><span data-stu-id="8b7fc-108">Name</span></span>    | <span data-ttu-id="8b7fc-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="8b7fc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8b7fc-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="8b7fc-110">Scope</span></span>   |<span data-ttu-id="8b7fc-111">Edge</span><span class="sxs-lookup"><span data-stu-id="8b7fc-111">Edge</span></span>|
|<span data-ttu-id="8b7fc-112">Version</span><span class="sxs-lookup"><span data-stu-id="8b7fc-112">Version</span></span>|<span data-ttu-id="8b7fc-113">4,5</span><span class="sxs-lookup"><span data-stu-id="8b7fc-113">4.5</span></span>|
|<span data-ttu-id="8b7fc-114">Type</span><span class="sxs-lookup"><span data-stu-id="8b7fc-114">Type</span></span>|<span data-ttu-id="8b7fc-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="8b7fc-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8b7fc-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="8b7fc-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
