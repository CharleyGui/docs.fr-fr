---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617229"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="4378c-101">Dans WPF, TextBox.Text et la liaison de données peuvent être désynchronisés</span><span class="sxs-lookup"><span data-stu-id="4378c-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="4378c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4378c-102">Details</span></span>

<span data-ttu-id="4378c-103">Dans certains cas, la propriété <xref:System.Windows.Controls.TextBox.Text> reflète une valeur précédente de la propriété liée aux données si cette propriété est modifiée au cours d'une opération d'écriture de liaison de données.</span><span class="sxs-lookup"><span data-stu-id="4378c-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4378c-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4378c-104">Suggestion</span></span>

<span data-ttu-id="4378c-105">Cela ne doit pas avoir d'impact négatif.</span><span class="sxs-lookup"><span data-stu-id="4378c-105">This should have no negative impact.</span></span> <span data-ttu-id="4378c-106">Vous pouvez, cependant, restaurer le comportement précédent en affectant à la propriété <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="4378c-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="4378c-107">Nom</span><span class="sxs-lookup"><span data-stu-id="4378c-107">Name</span></span>    | <span data-ttu-id="4378c-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="4378c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4378c-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="4378c-109">Scope</span></span>   | <span data-ttu-id="4378c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="4378c-110">Edge</span></span>        |
| <span data-ttu-id="4378c-111">Version</span><span class="sxs-lookup"><span data-stu-id="4378c-111">Version</span></span> | <span data-ttu-id="4378c-112">4,5</span><span class="sxs-lookup"><span data-stu-id="4378c-112">4.5</span></span>         |
|<span data-ttu-id="4378c-113">Type</span><span class="sxs-lookup"><span data-stu-id="4378c-113">Type</span></span>|<span data-ttu-id="4378c-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="4378c-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4378c-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="4378c-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
