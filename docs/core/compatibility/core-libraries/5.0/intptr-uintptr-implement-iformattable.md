---
title: 'Modification avec rupture : IntPtr et UIntPtr implémentent IFormattable'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où IntPtr et UIntPtr implémentent désormais IFormattable.
ms.date: 11/01/2020
ms.openlocfilehash: 0684652cdc2b8cf1d237074263bf0809082b0dcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761190"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="423d3-103">IntPtr et UIntPtr implémentent IFormattable</span><span class="sxs-lookup"><span data-stu-id="423d3-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="423d3-104"><xref:System.IntPtr> et <xref:System.UIntPtr> implémentent désormais <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="423d3-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="423d3-105">Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.</span><span class="sxs-lookup"><span data-stu-id="423d3-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="423d3-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="423d3-106">Change description</span></span>

<span data-ttu-id="423d3-107">Dans les versions précédentes de .NET, <xref:System.IntPtr> et <xref:System.UIntPtr> n’implémentent pas <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="423d3-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="423d3-108">Les fonctions qui recherchent <xref:System.IFormattable> peuvent revenir au simple appel à <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> ou, ce qui <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> signifie que les spécificateurs de format et les cultures ne sont pas respectés.</span><span class="sxs-lookup"><span data-stu-id="423d3-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="423d3-109">Dans .NET 5,0 et versions ultérieures, <xref:System.IntPtr> et <xref:System.UIntPtr> implémentent <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="423d3-109">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="423d3-110">Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.</span><span class="sxs-lookup"><span data-stu-id="423d3-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="423d3-111">Cette modification a un impact sur les scénarios tels que les chaînes interpolées et <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , entre autres.</span><span class="sxs-lookup"><span data-stu-id="423d3-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="423d3-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="423d3-112">Reason for change</span></span>

<span data-ttu-id="423d3-113"><xref:System.IntPtr> et <xref:System.UIntPtr> prennent désormais en charge le langage en C# via les `nint` `nuint` Mots clés et.</span><span class="sxs-lookup"><span data-stu-id="423d3-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="423d3-114">Les types de stockage ont été mis à jour pour fournir une parité proche (dans la mesure du possible) avec des fonctionnalités exposées par d’autres types primitifs, tels que <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="423d3-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="423d3-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="423d3-115">Version introduced</span></span>

<span data-ttu-id="423d3-116">5.0</span><span class="sxs-lookup"><span data-stu-id="423d3-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="423d3-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="423d3-117">Recommended action</span></span>

<span data-ttu-id="423d3-118">Si vous ne souhaitez pas qu’un spécificateur de format ou une culture personnalisée soit utilisé lors de l’affichage des valeurs de ces types, vous pouvez appeler les <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> surcharges et de `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="423d3-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="423d3-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="423d3-119">Affected APIs</span></span>

<span data-ttu-id="423d3-120">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="423d3-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
