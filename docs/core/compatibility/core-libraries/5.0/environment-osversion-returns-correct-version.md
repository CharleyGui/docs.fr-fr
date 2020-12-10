---
title: 'Modification avec rupture : Environment. OSVersion retourne la version appropriée du système d’exploitation'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où environnement. OSVersion retourne la version réelle du système d’exploitation au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009519"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="feca3-103">Environment. OSVersion retourne la version appropriée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="feca3-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="feca3-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation (OS) au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.</span><span class="sxs-lookup"><span data-stu-id="feca3-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="feca3-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="feca3-105">Change description</span></span>

<span data-ttu-id="feca3-106">Dans les versions précédentes de .NET, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne une version du système d’exploitation qui peut être incorrecte lorsqu’une application s’exécute en mode de compatibilité Windows.</span><span class="sxs-lookup"><span data-stu-id="feca3-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="feca3-107">Pour plus d’informations, consultez Remarques sur la [fonction GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="feca3-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="feca3-108">Sur macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version de noyau Darwin sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="feca3-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="feca3-109">À compter de .NET 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation pour Windows et MacOS.</span><span class="sxs-lookup"><span data-stu-id="feca3-109">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="feca3-110">Le tableau suivant montre la différence de comportement.</span><span class="sxs-lookup"><span data-stu-id="feca3-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="feca3-111">Versions antérieures de .NET</span><span class="sxs-lookup"><span data-stu-id="feca3-111">Previous .NET versions</span></span> | <span data-ttu-id="feca3-112">.NET 5 +</span><span class="sxs-lookup"><span data-stu-id="feca3-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="feca3-113">Windows</span><span class="sxs-lookup"><span data-stu-id="feca3-113">Windows</span></span> | <span data-ttu-id="feca3-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="feca3-114">6.2.9200.0</span></span> | <span data-ttu-id="feca3-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="feca3-115">10.0.19042.0</span></span> |
| <span data-ttu-id="feca3-116">macOS</span><span class="sxs-lookup"><span data-stu-id="feca3-116">macOS</span></span> | <span data-ttu-id="feca3-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="feca3-117">19.6.0.0</span></span> | <span data-ttu-id="feca3-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="feca3-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="feca3-119">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="feca3-119">Reason for change</span></span>

<span data-ttu-id="feca3-120">Les utilisateurs de cette propriété s’attendent à ce qu’elle retourne la version réelle du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="feca3-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="feca3-121">La plupart des applications .NET ne spécifient pas leur version prise en charge dans leur manifeste d’application, et obtiennent donc la version prise en charge par défaut à partir de l’hôte dotnet.</span><span class="sxs-lookup"><span data-stu-id="feca3-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="feca3-122">Par conséquent, le shim de compatibilité est rarement significatif pour l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="feca3-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="feca3-123">Lorsque Windows publie une nouvelle version et qu’un ancien hôte dotnet est toujours en cours d’utilisation, ces applications peuvent obtenir une version incorrecte du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="feca3-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="feca3-124">Le retour de la version réelle est plus Inline avec les attentes des développeurs de cette API.</span><span class="sxs-lookup"><span data-stu-id="feca3-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="feca3-125">Avec l’introduction de <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> , <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> et <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> dans .net 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> a été modifié pour être cohérent pour Windows et MacOS.</span><span class="sxs-lookup"><span data-stu-id="feca3-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="feca3-126">Version introduite</span><span class="sxs-lookup"><span data-stu-id="feca3-126">Version introduced</span></span>

<span data-ttu-id="feca3-127">5.0</span><span class="sxs-lookup"><span data-stu-id="feca3-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="feca3-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="feca3-128">Recommended action</span></span>

<span data-ttu-id="feca3-129">Examinez et testez le code que utilise <xref:System.Environment.OSVersion?displayProperty=nameWithType> pour s’assurer qu’il se comporte comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="feca3-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="feca3-130">API affectées</span><span class="sxs-lookup"><span data-stu-id="feca3-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
