---
title: 'Modification avec rupture : catégorie Unicode modifiée pour certains caractères latin-1'
description: Découvrez les modifications avec rupture de globalisation dans .NET 5,0 où les méthodes Char renvoient désormais la catégorie Unicode correcte pour les caractères de la plage latin-1.
ms.date: 04/07/2020
ms.openlocfilehash: 8bd093a89857c83921fc0bf987348b529f74ce68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761286"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="4359d-103">Catégorie Unicode modifiée pour certains caractères latin-1</span><span class="sxs-lookup"><span data-stu-id="4359d-103">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="4359d-104"><xref:System.Char> les méthodes retournent désormais la catégorie Unicode correcte pour les caractères de la plage latin-1.</span><span class="sxs-lookup"><span data-stu-id="4359d-104"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="4359d-105">La catégorie correspond à celle de la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="4359d-105">The category matches that of the Unicode standard.</span></span>

## <a name="change-description"></a><span data-ttu-id="4359d-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="4359d-106">Change description</span></span>

<span data-ttu-id="4359d-107">Dans les versions précédentes de .NET, <xref:System.Char> les méthodes utilisaient une liste fixe de catégories Unicode pour les caractères de la plage latin-1.</span><span class="sxs-lookup"><span data-stu-id="4359d-107">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="4359d-108">Toutefois, la norme Unicode a modifié les catégories de certains de ces caractères, car ces API ont été implémentées, créant ainsi une différence.</span><span class="sxs-lookup"><span data-stu-id="4359d-108">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="4359d-109">En outre, il y avait également une différence entre <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> les API et, qui suivent la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="4359d-109">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="4359d-110">Dans .NET 5,0 et versions ultérieures, <xref:System.Char> les méthodes utilisent et retournent la catégorie Unicode qui correspond à la norme Unicode pour tous les caractères.</span><span class="sxs-lookup"><span data-stu-id="4359d-110">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="4359d-111">Le tableau suivant indique les caractères dont les catégories Unicode ont changé dans .NET 5,0 :</span><span class="sxs-lookup"><span data-stu-id="4359d-111">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="4359d-112">Caractère</span><span class="sxs-lookup"><span data-stu-id="4359d-112">Character</span></span>    | <span data-ttu-id="4359d-113">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="4359d-113">Unicode category</span></span><br><span data-ttu-id="4359d-114">dans les versions précédentes de .NET</span><span class="sxs-lookup"><span data-stu-id="4359d-114">in previous .NET versions</span></span> | <span data-ttu-id="4359d-115">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="4359d-115">Unicode category</span></span><br><span data-ttu-id="4359d-116">dans .NET 5,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4359d-116">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="4359d-117">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="4359d-117">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="4359d-118">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="4359d-118">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="4359d-119">DISCRET (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="4359d-119">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="4359d-120">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="4359d-120">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="4359d-121">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="4359d-121">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a><span data-ttu-id="4359d-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4359d-122">Version introduced</span></span>

<span data-ttu-id="4359d-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4359d-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4359d-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4359d-124">Recommended action</span></span>

<span data-ttu-id="4359d-125">Si vous avez du code qui obtient la catégorie de caractères Unicode à l’aide de la <xref:System.Char> classe et suppose que la catégorie ne changera jamais, vous devrez peut-être la mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="4359d-125">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4359d-126">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="4359d-126">Reason for change</span></span>

<span data-ttu-id="4359d-127">Cette modification a été apportée afin que les catégories retournées par le <xref:System.Char> type soient cohérentes avec la norme Unicode et le <xref:System.Globalization.CharUnicodeInfo> type.</span><span class="sxs-lookup"><span data-stu-id="4359d-127">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4359d-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="4359d-128">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="4359d-129">En outre, toute classe qui dépend de <xref:System.Char> pour obtenir la catégorie de caractères Unicode, par exemple, <xref:System.Text.RegularExpressions.Regex> , est affectée par cette modification.</span><span class="sxs-lookup"><span data-stu-id="4359d-129">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
