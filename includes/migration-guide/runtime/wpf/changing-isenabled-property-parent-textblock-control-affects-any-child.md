---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496201"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="7f91b-101">La modification de la propriété IsEnabled du parent d’un contrôle TextBlock affecte tous les contrôles enfants</span><span class="sxs-lookup"><span data-stu-id="7f91b-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="7f91b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7f91b-102">Details</span></span>

<span data-ttu-id="7f91b-103">À compter du.NET Framework 4.6.2, la modification de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> affecte tous les contrôles enfants (comme les liens hypertexte et les boutons) du contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>. Dans le .NET Framework 4.6.1 et antérieur, les contrôles à l’intérieur d’une <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ne reflétaient pas toujours l’état de la propriété <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> du parent de <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7f91b-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f91b-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7f91b-104">Suggestion</span></span>

<span data-ttu-id="7f91b-105">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7f91b-105">None.</span></span> <span data-ttu-id="7f91b-106">Cette modification est conforme au comportement attendu pour les contrôles à l’intérieur d’un contrôle <xref:System.Windows.Controls.TextBlock?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7f91b-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="7f91b-107">Name</span><span class="sxs-lookup"><span data-stu-id="7f91b-107">Name</span></span>    | <span data-ttu-id="7f91b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="7f91b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f91b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="7f91b-109">Scope</span></span>   |<span data-ttu-id="7f91b-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="7f91b-110">Minor</span></span>|
|<span data-ttu-id="7f91b-111">Version</span><span class="sxs-lookup"><span data-stu-id="7f91b-111">Version</span></span>|<span data-ttu-id="7f91b-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7f91b-112">4.6.2</span></span>|
|<span data-ttu-id="7f91b-113">Type</span><span class="sxs-lookup"><span data-stu-id="7f91b-113">Type</span></span>|<span data-ttu-id="7f91b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="7f91b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7f91b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="7f91b-115">Affected APIs</span></span>

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
