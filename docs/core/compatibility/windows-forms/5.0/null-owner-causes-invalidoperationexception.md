---
title: 'Modification avec rupture : les API liées à DataGridView lèvent InvalidOperationException'
description: Découvrez la modification avec rupture dans .NET 5,0 où certaines API liées à DataGridView lèvent une exception si la valeur DataGridViewCellAccessibleObject. Owner de l’objet est null.
ms.date: 09/18/2020
ms.openlocfilehash: 927b1c9160700159a45aa1472b8d96f1a9ecfe25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761147"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="79f6e-103">Les API liées à DataGridView lèvent désormais InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="79f6e-103">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="79f6e-104">Certaines API liées à <xref:System.Windows.Forms.DataGridView> lèvent désormais une <xref:System.InvalidOperationException> si la valeur de l’objet <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> est `null` .</span><span class="sxs-lookup"><span data-stu-id="79f6e-104">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

## <a name="change-description"></a><span data-ttu-id="79f6e-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="79f6e-105">Change description</span></span>

<span data-ttu-id="79f6e-106">Dans les versions précédentes de .NET, les API affectées lèvent une <xref:System.NullReferenceException> lorsqu’elles sont appelées et la <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> valeur est `null` .</span><span class="sxs-lookup"><span data-stu-id="79f6e-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="79f6e-107">À compter de .NET 5,0, ces API lèvent un <xref:System.InvalidOperationException> au lieu d’un <xref:System.NullReferenceException> si la <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> valeur est `null` quand elles sont appelées.</span><span class="sxs-lookup"><span data-stu-id="79f6e-107">Starting in .NET 5.0, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="79f6e-108">La levée d’une <xref:System.InvalidOperationException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="79f6e-108">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="79f6e-109">Il améliore également l’expérience de débogage en communiquant clairement la propriété non valide.</span><span class="sxs-lookup"><span data-stu-id="79f6e-109">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="79f6e-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="79f6e-110">Version introduced</span></span>

<span data-ttu-id="79f6e-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="79f6e-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="79f6e-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="79f6e-112">Recommended action</span></span>

<span data-ttu-id="79f6e-113">Passez en revue votre code et, si nécessaire, mettez-le à jour pour empêcher la construction des types affectés avec la <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> propriété en tant que `null` .</span><span class="sxs-lookup"><span data-stu-id="79f6e-113">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="79f6e-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="79f6e-114">Affected APIs</span></span>

<span data-ttu-id="79f6e-115">Le tableau suivant répertorie les propriétés et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="79f6e-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="79f6e-116">Méthode ou propriété affectée</span><span class="sxs-lookup"><span data-stu-id="79f6e-116">Affected method or property</span></span> | <span data-ttu-id="79f6e-117">Propriété validée</span><span class="sxs-lookup"><span data-stu-id="79f6e-117">Validated property</span></span> | <span data-ttu-id="79f6e-118">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="79f6e-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-119">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-120">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-121">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-122">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-123">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-124">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-125">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-126">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-127">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-128">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-129">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="79f6e-130">5.0</span><span class="sxs-lookup"><span data-stu-id="79f6e-130">5.0</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

### Category

Windows Forms

-->
