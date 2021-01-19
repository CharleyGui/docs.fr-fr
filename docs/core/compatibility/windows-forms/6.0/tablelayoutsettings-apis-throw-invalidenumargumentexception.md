---
title: 'Modification avec rupture : certaines propriétés TableLayoutSettings lèvent InvalidEnumArgumentException'
description: Découvrez la modification avec rupture dans .NET 6,0 où certaines API TableLayoutSettings lèvent désormais une InvalidEnumArgumentException pour les arguments non valides.
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570268"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a><span data-ttu-id="48a1f-103">Les propriétés TableLayoutSettings sélectionnées lèvent InvalidEnumArgumentException</span><span class="sxs-lookup"><span data-stu-id="48a1f-103">Selected TableLayoutSettings properties throw InvalidEnumArgumentException</span></span>

<span data-ttu-id="48a1f-104">Les <xref:System.Windows.Forms.TableLayoutSettings> propriétés sélectionnées lèvent désormais une exception <xref:System.ComponentModel.InvalidEnumArgumentException> si vous tentez d’assigner une valeur incorrecte.</span><span class="sxs-lookup"><span data-stu-id="48a1f-104">Selected <xref:System.Windows.Forms.TableLayoutSettings> properties now throw an <xref:System.ComponentModel.InvalidEnumArgumentException> if you attempt to assign an incorrect value.</span></span>

## <a name="change-description"></a><span data-ttu-id="48a1f-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="48a1f-105">Change description</span></span>

<span data-ttu-id="48a1f-106">Dans les versions précédentes de .NET, ces propriétés lèvent une exception <xref:System.ArgumentOutOfRangeException> si vous tentez d’assigner une valeur incorrecte.</span><span class="sxs-lookup"><span data-stu-id="48a1f-106">In previous .NET versions, these properties throw an <xref:System.ArgumentOutOfRangeException> if you attempt to assign an incorrect value.</span></span> <span data-ttu-id="48a1f-107">À compter de .NET 6,0, ces propriétés lèvent un <xref:System.ComponentModel.InvalidEnumArgumentException> dans de tels cas.</span><span class="sxs-lookup"><span data-stu-id="48a1f-107">Starting in .NET 6.0, these properties throw an <xref:System.ComponentModel.InvalidEnumArgumentException> in such cases.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="48a1f-108">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="48a1f-108">Reason for change</span></span>

<span data-ttu-id="48a1f-109"><xref:System.ComponentModel.InvalidEnumArgumentException>La levée est conforme à l’API Windows Forms existante dans des situations similaires.</span><span class="sxs-lookup"><span data-stu-id="48a1f-109">Throwing <xref:System.ComponentModel.InvalidEnumArgumentException> is in line with the existing Windows Forms API in similar situations.</span></span> <span data-ttu-id="48a1f-110">La levée de cette exception offre également aux développeurs une meilleure expérience de débogage.</span><span class="sxs-lookup"><span data-stu-id="48a1f-110">Throwing this exception also provides developers with a better debug experience.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="48a1f-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="48a1f-111">Version introduced</span></span>

<span data-ttu-id="48a1f-112">.NET 6,0</span><span class="sxs-lookup"><span data-stu-id="48a1f-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="48a1f-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="48a1f-113">Recommended action</span></span>

- <span data-ttu-id="48a1f-114">Mettez à jour le code pour empêcher d’assigner des valeurs incorrectes.</span><span class="sxs-lookup"><span data-stu-id="48a1f-114">Update the code to prevent assigning incorrect values.</span></span>
- <span data-ttu-id="48a1f-115">Si nécessaire, gérez une <xref:System.ComponentModel.InvalidEnumArgumentException> lors de l’accès à ces API.</span><span class="sxs-lookup"><span data-stu-id="48a1f-115">If necessary, handle an <xref:System.ComponentModel.InvalidEnumArgumentException> when accessing these APIs.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="48a1f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="48a1f-116">Affected APIs</span></span>

<span data-ttu-id="48a1f-117">Le tableau suivant répertorie les propriétés affectées :</span><span class="sxs-lookup"><span data-stu-id="48a1f-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="48a1f-118">Propriété</span><span class="sxs-lookup"><span data-stu-id="48a1f-118">Property</span></span> | <span data-ttu-id="48a1f-119">Version modifiée</span><span class="sxs-lookup"><span data-stu-id="48a1f-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | <span data-ttu-id="48a1f-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="48a1f-120">Preview 1</span></span> |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | <span data-ttu-id="48a1f-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="48a1f-121">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
