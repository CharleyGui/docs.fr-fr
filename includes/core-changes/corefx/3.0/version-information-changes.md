---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344455"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="0a1eb-101">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="0a1eb-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="0a1eb-102">La plupart des API qui retournent des versions dans .NET Core retournent désormais la version du produit plutôt que la version du fichier.</span><span class="sxs-lookup"><span data-stu-id="0a1eb-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0a1eb-103">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="0a1eb-103">Change description</span></span>

<span data-ttu-id="0a1eb-104">Dans .NET Core 2,2 et versions antérieures, les méthodes telles que <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>et la boîte de dialogue des propriétés de fichier pour les assemblys .NET Core reflètent la version du fichier.</span><span class="sxs-lookup"><span data-stu-id="0a1eb-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="0a1eb-105">À compter de .NET Core 3,0, ils reflètent la version du produit.</span><span class="sxs-lookup"><span data-stu-id="0a1eb-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="0a1eb-106">La figure suivante illustre la différence dans les informations de version de l’assembly *System. Runtime. dll* pour .net Core 2,2 (à gauche) et .net Core 3,0 (à droite), tel qu’affiché dans la boîte de dialogue des propriétés du fichier de l' **Explorateur Windows** .</span><span class="sxs-lookup"><span data-stu-id="0a1eb-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="0a1eb-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0a1eb-108">Version introduced</span></span>

<span data-ttu-id="0a1eb-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0a1eb-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a1eb-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0a1eb-110">Recommended action</span></span>

<span data-ttu-id="0a1eb-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0a1eb-111">None.</span></span> <span data-ttu-id="0a1eb-112">Cette modification doit rendre la détection de version intuitive plutôt que abstruse.</span><span class="sxs-lookup"><span data-stu-id="0a1eb-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="0a1eb-113">Catégorie</span><span class="sxs-lookup"><span data-stu-id="0a1eb-113">Category</span></span>

<span data-ttu-id="0a1eb-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0a1eb-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a1eb-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="0a1eb-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
