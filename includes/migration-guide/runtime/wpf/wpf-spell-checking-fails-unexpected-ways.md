---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621792"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="27989-101">La correction orthographique dans WPF échoue de façon inattendue</span><span class="sxs-lookup"><span data-stu-id="27989-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="27989-102">Détails</span><span class="sxs-lookup"><span data-stu-id="27989-102">Details</span></span>

<span data-ttu-id="27989-103">Ceci inclut plusieurs problèmes du vérificateur orthographique de WPF :</span><span class="sxs-lookup"><span data-stu-id="27989-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="27989-104">Le vérificateur orthographique de WPF lève parfois <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="27989-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="27989-105">Le vérificateur orthographique de WPF échoue avec <xref:System.UnauthorizedAccessException> quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur »</span><span class="sxs-lookup"><span data-stu-id="27989-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="27989-106">Le vérificateur orthographique de WPF identifie incorrectement des fautes d’orthographe dans les mots composés, comme « Hausnummer » en allemand.</span><span class="sxs-lookup"><span data-stu-id="27989-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="27989-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="27989-107">Suggestion</span></span>

<span data-ttu-id="27989-108">Problème n° 1 : ce problème a été corrigé dans le .NET Framework 4.6.2. Problème n° 2 : le vérificateur orthographique de WPF n’est plus pris en charge quand les applications sont lancées avec « Exécuter en tant qu’autre utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="27989-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="27989-109">À compter du .NET Framework 4.6.2, les applications lancées de cette manière ne plantent plus de façon inattendue : à la place, le vérificateur orthographique est désactivé en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="27989-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="27989-110">Problème n° 3 : ce problème a été corrigé dans le .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="27989-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="27989-111">Nom</span><span class="sxs-lookup"><span data-stu-id="27989-111">Name</span></span>    | <span data-ttu-id="27989-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="27989-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27989-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="27989-113">Scope</span></span>   |<span data-ttu-id="27989-114">Edge</span><span class="sxs-lookup"><span data-stu-id="27989-114">Edge</span></span>|
|<span data-ttu-id="27989-115">Version</span><span class="sxs-lookup"><span data-stu-id="27989-115">Version</span></span>|<span data-ttu-id="27989-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="27989-116">4.6.1</span></span>|
|<span data-ttu-id="27989-117">Type</span><span class="sxs-lookup"><span data-stu-id="27989-117">Type</span></span>|<span data-ttu-id="27989-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="27989-118">Runtime</span></span>|
