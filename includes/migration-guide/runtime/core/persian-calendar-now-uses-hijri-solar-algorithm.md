---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621287"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="9e8fe-101">Le calendrier persan utilise désormais l’algorithme solaire hégirien</span><span class="sxs-lookup"><span data-stu-id="9e8fe-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="9e8fe-102">Détails</span><span class="sxs-lookup"><span data-stu-id="9e8fe-102">Details</span></span>

<span data-ttu-id="9e8fe-103">À compter de .NET Framework 4.6, la classe <xref:System.Globalization.PersianCalendar?displayProperty=fullName> utilise l’algorithme solaire hégirien.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="9e8fe-104">La conversion de dates entre le calendrier <xref:System.Globalization.PersianCalendar?displayProperty=fullName> et les autres calendriers peut produire un résultat légèrement différent à compter de .NET Framework 4.6 pour les dates antérieures à 1800 ou postérieures à 2023 (calendrier grégorien). De plus, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> est désormais <code>March 22, 0622</code> au lieu de <code>March 21, 0622</code>.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9e8fe-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="9e8fe-105">Suggestion</span></span>

<span data-ttu-id="9e8fe-106">Notez que certaines dates anciennes ou futures peuvent être légèrement différentes quand vous utilisez le calendrier persan dans .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="9e8fe-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="9e8fe-107">En outre, quand vous sérialisez des dates dans plusieurs processus qui peuvent s’exécuter sur des versions différentes du .NET Framework, ne les stockez pas sous forme de chaînes de date PersianCalendar (puisque ces valeurs peuvent être différentes).</span><span class="sxs-lookup"><span data-stu-id="9e8fe-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="9e8fe-108">Nom</span><span class="sxs-lookup"><span data-stu-id="9e8fe-108">Name</span></span>    | <span data-ttu-id="9e8fe-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="9e8fe-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9e8fe-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="9e8fe-110">Scope</span></span>   |<span data-ttu-id="9e8fe-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="9e8fe-111">Minor</span></span>|
|<span data-ttu-id="9e8fe-112">Version</span><span class="sxs-lookup"><span data-stu-id="9e8fe-112">Version</span></span>|<span data-ttu-id="9e8fe-113">4.6</span><span class="sxs-lookup"><span data-stu-id="9e8fe-113">4.6</span></span>|
|<span data-ttu-id="9e8fe-114">Type</span><span class="sxs-lookup"><span data-stu-id="9e8fe-114">Type</span></span>|<span data-ttu-id="9e8fe-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="9e8fe-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9e8fe-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="9e8fe-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
