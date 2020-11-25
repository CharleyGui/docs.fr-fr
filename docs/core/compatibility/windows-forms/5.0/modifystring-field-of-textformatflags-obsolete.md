---
title: 'Modification avec rupture : TextFormatFlags. ModifyString est obsolète'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où le champ TextFormatFlags. ModifyString est obsolète comme un avertissement.
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760916"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="9a561-103">TextFormatFlags. ModifyString est obsolète</span><span class="sxs-lookup"><span data-stu-id="9a561-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="9a561-104">Le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ est obsolète, comme un avertissement, et peut être supprimé dans une prochaine version .net.</span><span class="sxs-lookup"><span data-stu-id="9a561-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="9a561-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9a561-105">Change description</span></span>

<span data-ttu-id="9a561-106">Dans les versions précédentes de .NET, le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ d’énumération n’est pas marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="9a561-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="9a561-107">Dans .NET 5,0 et versions ultérieures, il est marqué comme étant obsolète en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="9a561-107">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="9a561-108">Ce champ peut être supprimé dans une future version .NET.</span><span class="sxs-lookup"><span data-stu-id="9a561-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9a561-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="9a561-109">Reason for change</span></span>

<span data-ttu-id="9a561-110">Le passage d’une chaîne à <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> avec <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> modifie la chaîne dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="9a561-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="9a561-111">Ce comportement interrompt la promesse de la chaîne d’immuabilité et peut entraîner une altération irrécupérable de l’état du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="9a561-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9a561-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9a561-112">Version introduced</span></span>

<span data-ttu-id="9a561-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9a561-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9a561-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9a561-114">Recommended action</span></span>

<span data-ttu-id="9a561-115">Mettez à jour le code qui s’appuie sur <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9a561-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9a561-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a561-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
