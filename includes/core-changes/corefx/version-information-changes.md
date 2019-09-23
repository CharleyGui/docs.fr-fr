---
ms.openlocfilehash: 5bed2d1d4eda4a4c577f05f614a71aa9180998a7
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181986"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="c8b6f-101">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="c8b6f-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="c8b6f-102">La plupart des API qui retournent des versions dans .NET Core retournaient désormais la version du produit plutôt que la version du fichier.</span><span class="sxs-lookup"><span data-stu-id="c8b6f-102">Many of the APIs that return versions in .NET Core now returned the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c8b6f-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="c8b6f-103">Change description</span></span>

<span data-ttu-id="c8b6f-104">Dans .net Core 2,2 et versions antérieures, les méthodes telles <xref:System.Environment.Version?displayProperty=nameWithType>que <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, et la boîte de dialogue des propriétés de fichier pour les assemblys .net Core reflètent la version de fichier.</span><span class="sxs-lookup"><span data-stu-id="c8b6f-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="c8b6f-105">À compter de .NET Core 3,0, ils reflètent la version du produit.</span><span class="sxs-lookup"><span data-stu-id="c8b6f-105">Starting with .NET Core 3.0, they reflect the product version.</span></span> 

<span data-ttu-id="c8b6f-106">La figure suivante illustre la différence dans les informations de version de l’assembly *System. Runtime. dll* pour .net Core 2,2 (à gauche) et .net Core 3,0 (à droite), tel qu’affiché dans la boîte de dialogue des propriétés du fichier de l' **Explorateur Windows** .</span><span class="sxs-lookup"><span data-stu-id="c8b6f-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="c8b6f-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c8b6f-108">Version introduced</span></span>

<span data-ttu-id="c8b6f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="c8b6f-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c8b6f-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c8b6f-110">Recommended action</span></span>

<span data-ttu-id="c8b6f-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c8b6f-111">None.</span></span> <span data-ttu-id="c8b6f-112">Cette modification doit rendre la détection de version intuitive plutôt que abstruse.</span><span class="sxs-lookup"><span data-stu-id="c8b6f-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="c8b6f-113">Category</span><span class="sxs-lookup"><span data-stu-id="c8b6f-113">Category</span></span>

<span data-ttu-id="c8b6f-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c8b6f-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c8b6f-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="c8b6f-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`


-->