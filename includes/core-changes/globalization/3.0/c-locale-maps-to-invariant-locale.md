---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567781"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="b3d09-101">Cartes locales "C" à l’invariant local</span><span class="sxs-lookup"><span data-stu-id="b3d09-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="b3d09-102">.NET Core 2.2 et les versions antérieures dépendent du comportement par défaut de l’USI, qui cartographie le lieu "C" au en_US_POSIX local.</span><span class="sxs-lookup"><span data-stu-id="b3d09-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="b3d09-103">Le en_US_POSIX local a un comportement de collation indésirable, car il ne prend pas en charge les comparaisons de chaînes insensibles au cas.</span><span class="sxs-lookup"><span data-stu-id="b3d09-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="b3d09-104">Parce que certaines distributions Linux définir le "C" local comme le lieu par défaut, les utilisateurs ont connu un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="b3d09-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3d09-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b3d09-105">Change description</span></span>

<span data-ttu-id="b3d09-106">En commençant par .NET Core 3.0, la cartographie locale "C" a changé pour utiliser le local invariant au lieu de en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="b3d09-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="b3d09-107">Le local "C" à la cartographie invariante est également appliqué à Windows pour la cohérence.</span><span class="sxs-lookup"><span data-stu-id="b3d09-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="b3d09-108">La cartographie du « C » pour en_US_POSIX culture a causé la confusion des clients, parce que en_US_POSIX ne prend pas en charge les opérations insensibles de tri/de chaîne de recherche de cas.</span><span class="sxs-lookup"><span data-stu-id="b3d09-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="b3d09-109">Parce que le "C" local est utilisé comme un lieu par défaut dans certains des distros Linux, les clients ont connu ce comportement indésirable sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b3d09-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3d09-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b3d09-110">Version introduced</span></span>

<span data-ttu-id="b3d09-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b3d09-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="b3d09-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b3d09-112">Recommended action</span></span>

<span data-ttu-id="b3d09-113">Rien de plus spécifique que la prise de conscience de ce changement.</span><span class="sxs-lookup"><span data-stu-id="b3d09-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="b3d09-114">Ce changement n’affecte que les applications qui utilisent la cartographie locale « C ».</span><span class="sxs-lookup"><span data-stu-id="b3d09-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="b3d09-115">Category</span><span class="sxs-lookup"><span data-stu-id="b3d09-115">Category</span></span>

<span data-ttu-id="b3d09-116">Globalisation</span><span class="sxs-lookup"><span data-stu-id="b3d09-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="b3d09-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="b3d09-117">Affected APIs</span></span>

<span data-ttu-id="b3d09-118">Toutes les API de collation et de culture sont affectées par ce changement.</span><span class="sxs-lookup"><span data-stu-id="b3d09-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
