---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024695"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="1aab4-101">IntPtr et UIntPtr implémentent IFormattable</span><span class="sxs-lookup"><span data-stu-id="1aab4-101">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="1aab4-102"><xref:System.IntPtr>et <xref:System.UIntPtr> implémentent désormais <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="1aab4-102"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="1aab4-103">Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.</span><span class="sxs-lookup"><span data-stu-id="1aab4-103">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1aab4-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1aab4-104">Change description</span></span>

<span data-ttu-id="1aab4-105">Dans les versions précédentes de .NET, <xref:System.IntPtr> et <xref:System.UIntPtr> n’implémentent pas <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="1aab4-105">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="1aab4-106">Les fonctions qui recherchent <xref:System.IFormattable> peuvent revenir au simple appel à <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> ou, ce qui <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> signifie que les spécificateurs de format et les cultures ne sont pas respectés.</span><span class="sxs-lookup"><span data-stu-id="1aab4-106">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="1aab4-107">Dans .NET 5,0 et versions ultérieures, <xref:System.IntPtr> et <xref:System.UIntPtr> implémentent <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="1aab4-107">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="1aab4-108">Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.</span><span class="sxs-lookup"><span data-stu-id="1aab4-108">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="1aab4-109">Cette modification a un impact sur les scénarios tels que les chaînes interpolées et <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , entre autres.</span><span class="sxs-lookup"><span data-stu-id="1aab4-109">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1aab4-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="1aab4-110">Reason for change</span></span>

<span data-ttu-id="1aab4-111"><xref:System.IntPtr>et <xref:System.UIntPtr> prennent désormais en charge le langage en C# via les `nint` `nuint` Mots clés et.</span><span class="sxs-lookup"><span data-stu-id="1aab4-111"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="1aab4-112">Les types de stockage ont été mis à jour pour fournir une parité proche (dans la mesure du possible) avec des fonctionnalités exposées par d’autres types primitifs, tels que <xref:System.Int32?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1aab4-112">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1aab4-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1aab4-113">Version introduced</span></span>

<span data-ttu-id="1aab4-114">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="1aab4-114">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1aab4-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1aab4-115">Recommended action</span></span>

<span data-ttu-id="1aab4-116">Si vous ne souhaitez pas qu’un spécificateur de format ou une culture personnalisée soit utilisé lors de l’affichage des valeurs de ces types, vous pouvez appeler les <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> surcharges et de `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="1aab4-116">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

#### <a name="category"></a><span data-ttu-id="1aab4-117">Category</span><span class="sxs-lookup"><span data-stu-id="1aab4-117">Category</span></span>

<span data-ttu-id="1aab4-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="1aab4-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1aab4-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="1aab4-119">Affected APIs</span></span>

<span data-ttu-id="1aab4-120">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="1aab4-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
