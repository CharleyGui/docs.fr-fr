---
title: 'Modification avec rupture : les propriétés WinForms lèvent désormais ArgumentOutOfRangeException'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où certaines propriétés de Windows Forms lèvent désormais une exception ArgumentOutOfRangeException pour les arguments non valides.
ms.date: 06/18/2020
ms.openlocfilehash: 94593047d16304ce401b23993ad4ca173c10812b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761111"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="88d08-103">Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="88d08-103">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="88d08-104">Certaines propriétés de Windows Forms lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="88d08-104">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="88d08-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="88d08-105">Change description</span></span>

<span data-ttu-id="88d08-106">Auparavant, ces propriétés relevaient d’autres exceptions, telles que <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> ou <xref:System.ArgumentException> , en cas de réussite des arguments hors limites.</span><span class="sxs-lookup"><span data-stu-id="88d08-106">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="88d08-107">À compter de .NET 5,0, ces propriétés lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> quand les arguments passés sont en dehors de la plage.</span><span class="sxs-lookup"><span data-stu-id="88d08-107">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="88d08-108">La levée d’une <xref:System.ArgumentOutOfRangeException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="88d08-108">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="88d08-109">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="88d08-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="88d08-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="88d08-110">Version introduced</span></span>

<span data-ttu-id="88d08-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="88d08-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="88d08-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="88d08-112">Recommended action</span></span>

- <span data-ttu-id="88d08-113">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="88d08-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="88d08-114">Si nécessaire, gérez une <xref:System.ArgumentOutOfRangeException> lors de la définition de la propriété.</span><span class="sxs-lookup"><span data-stu-id="88d08-114">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="88d08-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="88d08-115">Affected APIs</span></span>

<span data-ttu-id="88d08-116">Le tableau suivant répertorie les propriétés et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="88d08-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="88d08-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="88d08-117">Property</span></span> | <span data-ttu-id="88d08-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="88d08-118">Parameter name</span></span> | <span data-ttu-id="88d08-119">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="88d08-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="88d08-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="88d08-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="88d08-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="88d08-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="88d08-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="88d08-122">5.0 Preview 6</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
