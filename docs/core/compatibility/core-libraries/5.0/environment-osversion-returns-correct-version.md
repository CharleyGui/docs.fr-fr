---
title: 'Modification avec rupture : Environment. OSVersion retourne la version appropriée du système d’exploitation'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où environnement. OSVersion retourne la version réelle du système d’exploitation au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761308"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="cbd79-103">Environment. OSVersion retourne la version appropriée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="cbd79-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="cbd79-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation (OS) au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.</span><span class="sxs-lookup"><span data-stu-id="cbd79-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="cbd79-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="cbd79-105">Change description</span></span>

<span data-ttu-id="cbd79-106">Dans les versions précédentes de .NET, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne une version du système d’exploitation qui peut être incorrecte lorsqu’une application s’exécute en mode de compatibilité Windows.</span><span class="sxs-lookup"><span data-stu-id="cbd79-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="cbd79-107">Pour plus d’informations, consultez Remarques sur la [fonction GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="cbd79-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="cbd79-108">À compter de .NET 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cbd79-108">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="cbd79-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="cbd79-109">Reason for change</span></span>

<span data-ttu-id="cbd79-110">Les utilisateurs de cette propriété s’attendent à ce qu’elle retourne la version réelle du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cbd79-110">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="cbd79-111">La plupart des applications .NET ne spécifient pas leur version prise en charge dans leur manifeste d’application, et obtiennent donc la version prise en charge par défaut à partir de l’hôte dotnet.</span><span class="sxs-lookup"><span data-stu-id="cbd79-111">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="cbd79-112">Par conséquent, le shim de compatibilité est rarement significatif pour l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cbd79-112">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="cbd79-113">Lorsque Windows publie une nouvelle version et qu’un ancien hôte dotnet est toujours en cours d’utilisation, ces applications peuvent obtenir une version incorrecte du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cbd79-113">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="cbd79-114">Le retour de la version réelle est plus Inline avec les attentes des développeurs de cette API.</span><span class="sxs-lookup"><span data-stu-id="cbd79-114">Returning the actual version is more inline with developers' expectations of this API.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cbd79-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cbd79-115">Version introduced</span></span>

<span data-ttu-id="cbd79-116">5.0</span><span class="sxs-lookup"><span data-stu-id="cbd79-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cbd79-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cbd79-117">Recommended action</span></span>

<span data-ttu-id="cbd79-118">Examinez et testez le code que utilise <xref:System.Environment.OSVersion?displayProperty=nameWithType> pour s’assurer qu’il se comporte comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="cbd79-118">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="cbd79-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="cbd79-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
