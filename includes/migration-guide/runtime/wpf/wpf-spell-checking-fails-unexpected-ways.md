---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497876"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="3d366-101">La correction orthographique dans WPF échoue de façon inattendue</span><span class="sxs-lookup"><span data-stu-id="3d366-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="3d366-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3d366-102">Details</span></span>

<span data-ttu-id="3d366-103">Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :</span><span class="sxs-lookup"><span data-stu-id="3d366-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="3d366-104">Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3d366-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="3d366-105">Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</span><span class="sxs-lookup"><span data-stu-id="3d366-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="3d366-106">Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</span><span class="sxs-lookup"><span data-stu-id="3d366-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="3d366-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3d366-107">Suggestion</span></span>

<span data-ttu-id="3d366-108">Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="3d366-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="3d366-109">À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="3d366-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="3d366-110">Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="3d366-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="3d366-111">Name</span><span class="sxs-lookup"><span data-stu-id="3d366-111">Name</span></span>    | <span data-ttu-id="3d366-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="3d366-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d366-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="3d366-113">Scope</span></span>   |<span data-ttu-id="3d366-114">Edge</span><span class="sxs-lookup"><span data-stu-id="3d366-114">Edge</span></span>|
|<span data-ttu-id="3d366-115">Version</span><span class="sxs-lookup"><span data-stu-id="3d366-115">Version</span></span>|<span data-ttu-id="3d366-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3d366-116">4.6.1</span></span>|
|<span data-ttu-id="3d366-117">Type</span><span class="sxs-lookup"><span data-stu-id="3d366-117">Type</span></span>|<span data-ttu-id="3d366-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="3d366-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3d366-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="3d366-119">Affected APIs</span></span>

<span data-ttu-id="3d366-120">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="3d366-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
