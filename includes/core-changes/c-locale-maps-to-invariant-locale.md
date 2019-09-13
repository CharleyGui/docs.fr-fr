---
ms.openlocfilehash: 9e9e443be9ea51d214e95c676fc28f0d8790af8b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930067"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="9a0dc-101">Les paramètres régionaux « C » sont mappés aux paramètres régionaux invariants</span><span class="sxs-lookup"><span data-stu-id="9a0dc-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="9a0dc-102">.NET Core 2,2 et les versions antérieures dépendent du comportement ICU par défaut, qui mappe les paramètres régionaux « C » aux paramètres régionaux en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="9a0dc-103">Les paramètres régionaux en_US_POSIX ont un comportement de classement indésirable, car il ne prend pas en charge les comparaisons de chaînes ne respectant pas la casse.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="9a0dc-104">Étant donné que certaines distributions Linux définissent les paramètres régionaux « C » comme paramètres régionaux par défaut, les utilisateurs rencontraient un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span> 

#### <a name="details"></a><span data-ttu-id="9a0dc-105">Détails</span><span class="sxs-lookup"><span data-stu-id="9a0dc-105">Details</span></span>

<span data-ttu-id="9a0dc-106">À compter de .NET Core 3,0, le mappage de paramètres régionaux « C » a changé pour utiliser les paramètres régionaux invariants au lieu de en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="9a0dc-107">Les paramètres régionaux « C » du mappage invariant sont également appliqués à Windows pour des fins de cohérence.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="9a0dc-108">Le mappage de « C » à la culture en_US_POSIX a provoqué la confusion chez les clients, car en_US_POSIX ne prend pas en charge les opérations de chaîne de tri/recherche sans respect de la casse.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="9a0dc-109">Étant donné que les paramètres régionaux « C » sont utilisés comme paramètres régionaux par défaut dans certains distributions Linux, les clients ont rencontré ce comportement indésirable sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="9a0dc-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9a0dc-110">Version introduced</span></span>

<span data-ttu-id="9a0dc-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9a0dc-111">.NET Core 3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="9a0dc-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9a0dc-112">Recommended action</span></span>

<span data-ttu-id="9a0dc-113">Rien de plus spécifique que la connaissance de cette modification.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="9a0dc-114">Cette modification affecte uniquement les applications qui utilisent le mappage de paramètres régionaux « C ».</span><span class="sxs-lookup"><span data-stu-id="9a0dc-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="9a0dc-115">Catégorie</span><span class="sxs-lookup"><span data-stu-id="9a0dc-115">Category</span></span>

<span data-ttu-id="9a0dc-116">Globalisation</span><span class="sxs-lookup"><span data-stu-id="9a0dc-116">Globalization</span></span> 

### <a name="affected-apis"></a><span data-ttu-id="9a0dc-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a0dc-117">Affected APIs</span></span>

<span data-ttu-id="9a0dc-118">Toutes les API de classement et de culture sont affectées par cette modification.</span><span class="sxs-lookup"><span data-stu-id="9a0dc-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->