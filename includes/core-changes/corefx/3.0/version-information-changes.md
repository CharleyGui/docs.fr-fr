---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021557"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="249fa-101">API qui signalent la version du produit et non de la version du fichier</span><span class="sxs-lookup"><span data-stu-id="249fa-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="249fa-102">La plupart des API qui retournent des versions dans .NET Core retournent désormais la version du produit plutôt que la version du fichier.</span><span class="sxs-lookup"><span data-stu-id="249fa-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="249fa-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="249fa-103">Change description</span></span>

<span data-ttu-id="249fa-104">Dans .net Core 2,2 et versions antérieures, les méthodes telles <xref:System.Environment.Version?displayProperty=nameWithType>que <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, et la boîte de dialogue des propriétés de fichier pour les assemblys .net Core reflètent la version de fichier.</span><span class="sxs-lookup"><span data-stu-id="249fa-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="249fa-105">À compter de .NET Core 3,0, ils reflètent la version du produit.</span><span class="sxs-lookup"><span data-stu-id="249fa-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="249fa-106">La figure suivante illustre la différence dans les informations de version de l’assembly *System. Runtime. dll* pour .net Core 2,2 (à gauche) et .net Core 3,0 (à droite), tel qu’affiché dans la boîte de dialogue des propriétés du fichier de l' **Explorateur Windows** .</span><span class="sxs-lookup"><span data-stu-id="249fa-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="249fa-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="249fa-108">Version introduced</span></span>

<span data-ttu-id="249fa-109">3.0</span><span class="sxs-lookup"><span data-stu-id="249fa-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="249fa-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="249fa-110">Recommended action</span></span>

<span data-ttu-id="249fa-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="249fa-111">None.</span></span> <span data-ttu-id="249fa-112">Cette modification doit rendre la détection de version intuitive plutôt que abstruse.</span><span class="sxs-lookup"><span data-stu-id="249fa-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="249fa-113">Category</span><span class="sxs-lookup"><span data-stu-id="249fa-113">Category</span></span>

<span data-ttu-id="249fa-114">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="249fa-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="249fa-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="249fa-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
