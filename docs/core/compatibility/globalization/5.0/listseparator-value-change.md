---
title: 'Modification avec rupture : changement de valeur TextInfo. ListSeparator'
description: Découvrez la modification avec rupture .NET 5,0 où la valeur par défaut de TextInfo. ListSeparator a été modifiée entre les versions 5,0 et 5.0.1.
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596544"
---
# <a name="textinfolistseparator-values-changed"></a><span data-ttu-id="979b7-103">Valeurs de TextInfo. ListSeparator modifiées</span><span class="sxs-lookup"><span data-stu-id="979b7-103">TextInfo.ListSeparator values changed</span></span>

<span data-ttu-id="979b7-104">Les valeurs par défaut <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> pour les différentes cultures ont changé sur tous les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="979b7-104">The default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures have changed on all operating systems.</span></span>

## <a name="change-description"></a><span data-ttu-id="979b7-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="979b7-105">Change description</span></span>

<span data-ttu-id="979b7-106">Dans .NET 5.0.0, dans le cadre du [passage de nls aux bibliothèques ICU](icu-globalization-api.md), les valeurs par défaut <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> pour les différentes cultures ont changé sur Windows.</span><span class="sxs-lookup"><span data-stu-id="979b7-106">In .NET 5.0.0, as part of the [switch from NLS to ICU libraries](icu-globalization-api.md), the default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures changed on Windows.</span></span> <span data-ttu-id="979b7-107">Les valeurs de séparateur décimal, obtenues à partir des composants internationaux pour Unicode (ICU), ont été utilisées comme <xref:System.Globalization.TextInfo.ListSeparator> valeurs.</span><span class="sxs-lookup"><span data-stu-id="979b7-107">Decimal separator values, obtained from International Components for Unicode (ICU), were used as the <xref:System.Globalization.TextInfo.ListSeparator> values.</span></span> <span data-ttu-id="979b7-108">Sur Linux et macOS, aucune modification n’a été apportée aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs, c’est-à-dire qu’elles continuent à utiliser des valeurs de séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="979b7-108">On Linux and macOS, there was no change in <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values; that is, they continued to use decimal separator values.</span></span>

<span data-ttu-id="979b7-109">Pour tous les systèmes d’exploitation dans .NET 5.0.1 et versions ultérieures, les valeurs de <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> sont équivalentes aux valeurs qui seraient obtenues à partir de nls.</span><span class="sxs-lookup"><span data-stu-id="979b7-109">For all operating systems in .NET 5.0.1 and later versions, the values for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> are equivalent to the values that would be obtained from NLS.</span></span> <span data-ttu-id="979b7-110">Pour Windows, cela signifie que les valeurs sont équivalentes à ce qu’elles étaient dans .NET Framework et .NET Core 1,0-3,1.</span><span class="sxs-lookup"><span data-stu-id="979b7-110">For Windows, this means the values are equivalent to what they were in .NET Framework and .NET Core 1.0 - 3.1.</span></span> <span data-ttu-id="979b7-111">Pour Linux et macOS, les <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs correspondent maintenant aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs pour Windows.</span><span class="sxs-lookup"><span data-stu-id="979b7-111">For Linux and macOS, the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values now match the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for Windows.</span></span>

<span data-ttu-id="979b7-112">Le tableau suivant récapitule les modifications apportées aux <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs.</span><span class="sxs-lookup"><span data-stu-id="979b7-112">The following table summarizes the changes for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

| | <span data-ttu-id="979b7-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="979b7-113">.NET Framework</span></span><br/><span data-ttu-id="979b7-114">.NET Core 1,0-3,1</span><span class="sxs-lookup"><span data-stu-id="979b7-114">.NET Core 1.0 - 3.1</span></span> | <span data-ttu-id="979b7-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="979b7-115">.NET 5.0</span></span> | <span data-ttu-id="979b7-116">.NET 5.0.1</span><span class="sxs-lookup"><span data-stu-id="979b7-116">.NET 5.0.1</span></span> |
-|-|-|-
| <span data-ttu-id="979b7-117">**Windows**</span><span class="sxs-lookup"><span data-stu-id="979b7-117">**Windows**</span></span> | <span data-ttu-id="979b7-118">Obtenir à partir de NLS</span><span class="sxs-lookup"><span data-stu-id="979b7-118">Obtain from NLS</span></span> | <span data-ttu-id="979b7-119">Séparateur décimal d’ICU.</span><span class="sxs-lookup"><span data-stu-id="979b7-119">Decimal separator from ICU.</span></span><br/><span data-ttu-id="979b7-120">Peut revenir à NLS.</span><span class="sxs-lookup"><span data-stu-id="979b7-120">Can switch back to NLS.</span></span> | <span data-ttu-id="979b7-121">Équivalent à NLS</span><span class="sxs-lookup"><span data-stu-id="979b7-121">Equivalent to NLS</span></span> |
| <span data-ttu-id="979b7-122">**Linux et macOS**</span><span class="sxs-lookup"><span data-stu-id="979b7-122">**Linux and macOS**</span></span> | <span data-ttu-id="979b7-123">Séparateur décimal d’ICU</span><span class="sxs-lookup"><span data-stu-id="979b7-123">Decimal separator from ICU</span></span> | <span data-ttu-id="979b7-124">Séparateur décimal d’ICU</span><span class="sxs-lookup"><span data-stu-id="979b7-124">Decimal separator from ICU</span></span> | <span data-ttu-id="979b7-125">Équivalent à NLS</span><span class="sxs-lookup"><span data-stu-id="979b7-125">Equivalent to NLS</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="979b7-126">Version introduite</span><span class="sxs-lookup"><span data-stu-id="979b7-126">Version introduced</span></span>

<span data-ttu-id="979b7-127">5.0.1</span><span class="sxs-lookup"><span data-stu-id="979b7-127">5.0.1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="979b7-128">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="979b7-128">Reason for change</span></span>

<span data-ttu-id="979b7-129">Les développeurs ont signalé qu’ils utilisent la <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> propriété lors de l’analyse des fichiers de valeurs séparées par des virgules (CSV), et les nouvelles <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> valeurs ont enfreint cette analyse.</span><span class="sxs-lookup"><span data-stu-id="979b7-129">Developers reported that they use the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> property when parsing comma-separated value (CSV) files, and the new <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values broke that parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="979b7-130">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="979b7-130">Recommended action</span></span>

<span data-ttu-id="979b7-131">Si votre code s’appuie sur les valeurs de séparateur décimal précédentes, vous pouvez coder en dur les valeurs souhaitées <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="979b7-131">If your code relies on the previous decimal separator values, you can hardcode the desired <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="979b7-132">API affectées</span><span class="sxs-lookup"><span data-stu-id="979b7-132">Affected APIs</span></span>

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
