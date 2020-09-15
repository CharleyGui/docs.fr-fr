---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065060"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="fc6e2-101">Catégorie Unicode modifiée pour certains caractères latin-1</span><span class="sxs-lookup"><span data-stu-id="fc6e2-101">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="fc6e2-102"><xref:System.Char> les méthodes retournent désormais la catégorie Unicode correcte pour les caractères de la plage latin-1.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-102"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="fc6e2-103">La catégorie correspond à celle de la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-103">The category matches that of the Unicode standard.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc6e2-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fc6e2-104">Change description</span></span>

<span data-ttu-id="fc6e2-105">Dans les versions précédentes de .NET, <xref:System.Char> les méthodes utilisaient une liste fixe de catégories Unicode pour les caractères de la plage latin-1.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-105">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="fc6e2-106">Toutefois, la norme Unicode a modifié les catégories de certains de ces caractères, car ces API ont été implémentées, créant ainsi une différence.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-106">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="fc6e2-107">En outre, il y avait également une différence entre <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> les API et, qui suivent la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-107">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="fc6e2-108">Dans .NET 5,0 et versions ultérieures, <xref:System.Char> les méthodes utilisent et retournent la catégorie Unicode qui correspond à la norme Unicode pour tous les caractères.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-108">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="fc6e2-109">Le tableau suivant indique les caractères dont les catégories Unicode ont changé dans .NET 5,0 :</span><span class="sxs-lookup"><span data-stu-id="fc6e2-109">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="fc6e2-110">Caractère</span><span class="sxs-lookup"><span data-stu-id="fc6e2-110">Character</span></span>    | <span data-ttu-id="fc6e2-111">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="fc6e2-111">Unicode category</span></span><br><span data-ttu-id="fc6e2-112">dans les versions précédentes de .NET</span><span class="sxs-lookup"><span data-stu-id="fc6e2-112">in previous .NET versions</span></span> | <span data-ttu-id="fc6e2-113">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="fc6e2-113">Unicode category</span></span><br><span data-ttu-id="fc6e2-114">dans .NET 5,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="fc6e2-114">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="fc6e2-115">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="fc6e2-115">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="fc6e2-116">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="fc6e2-116">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="fc6e2-117">DISCRET (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="fc6e2-117">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="fc6e2-118">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="fc6e2-118">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="fc6e2-119">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="fc6e2-119">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a><span data-ttu-id="fc6e2-120">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc6e2-120">Version introduced</span></span>

<span data-ttu-id="fc6e2-121">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="fc6e2-121">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc6e2-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fc6e2-122">Recommended action</span></span>

<span data-ttu-id="fc6e2-123">Si vous avez du code qui obtient la catégorie de caractères Unicode à l’aide de la <xref:System.Char> classe et suppose que la catégorie ne changera jamais, vous devrez peut-être la mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-123">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fc6e2-124">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="fc6e2-124">Reason for change</span></span>

<span data-ttu-id="fc6e2-125">Cette modification a été apportée afin que les catégories retournées par le <xref:System.Char> type soient cohérentes avec la norme Unicode et le <xref:System.Globalization.CharUnicodeInfo> type.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-125">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

#### <a name="category"></a><span data-ttu-id="fc6e2-126">Category</span><span class="sxs-lookup"><span data-stu-id="fc6e2-126">Category</span></span>

- <span data-ttu-id="fc6e2-127">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc6e2-127">Core .NET libraries</span></span>
- <span data-ttu-id="fc6e2-128">Globalisation</span><span class="sxs-lookup"><span data-stu-id="fc6e2-128">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc6e2-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="fc6e2-129">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="fc6e2-130">En outre, toute classe qui dépend de <xref:System.Char> pour obtenir la catégorie de caractères Unicode, par exemple, <xref:System.Text.RegularExpressions.Regex> , est affectée par cette modification.</span><span class="sxs-lookup"><span data-stu-id="fc6e2-130">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
