---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558173"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="81d64-101">Environment. OSVersion retourne la version appropriée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="81d64-101">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="81d64-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation (OS) au lieu de, par exemple, le système d’exploitation sélectionné pour la compatibilité des applications.</span><span class="sxs-lookup"><span data-stu-id="81d64-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81d64-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="81d64-103">Change description</span></span>

<span data-ttu-id="81d64-104">Dans les versions précédentes de .NET, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne une version du système d’exploitation qui peut être incorrecte lorsqu’une application s’exécute en mode de compatibilité Windows.</span><span class="sxs-lookup"><span data-stu-id="81d64-104">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="81d64-105">Pour plus d’informations, consultez Remarques sur la [fonction GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="81d64-105">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="81d64-106">À compter de .NET 5,0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> retourne la version réelle du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="81d64-106">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="81d64-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="81d64-107">Reason for change</span></span>

<span data-ttu-id="81d64-108">Les utilisateurs de cette propriété s’attendent à ce qu’elle retourne la version réelle du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="81d64-108">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="81d64-109">La plupart des applications .NET ne spécifient pas leur version prise en charge dans leur manifeste d’application, et obtiennent donc la version prise en charge par défaut à partir de l’hôte dotnet.</span><span class="sxs-lookup"><span data-stu-id="81d64-109">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="81d64-110">Par conséquent, le shim de compatibilité est rarement significatif pour l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="81d64-110">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="81d64-111">Lorsque Windows publie une nouvelle version et qu’un ancien hôte dotnet est toujours en cours d’utilisation, ces applications peuvent obtenir une version incorrecte du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="81d64-111">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="81d64-112">Le retour de la version réelle est plus Inline avec les attentes des développeurs de cette API.</span><span class="sxs-lookup"><span data-stu-id="81d64-112">Returning the actual version is more inline with developers' expectations of this API.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81d64-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="81d64-113">Version introduced</span></span>

<span data-ttu-id="81d64-114">5.0</span><span class="sxs-lookup"><span data-stu-id="81d64-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81d64-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="81d64-115">Recommended action</span></span>

<span data-ttu-id="81d64-116">Examinez et testez le code que utilise <xref:System.Environment.OSVersion?displayProperty=nameWithType> pour s’assurer qu’il se comporte comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="81d64-116">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

#### <a name="category"></a><span data-ttu-id="81d64-117">Category</span><span class="sxs-lookup"><span data-stu-id="81d64-117">Category</span></span>

<span data-ttu-id="81d64-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="81d64-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81d64-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="81d64-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
