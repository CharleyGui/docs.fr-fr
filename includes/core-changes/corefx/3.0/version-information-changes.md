---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021557"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="4a9a3-101">API qui signalent la version signalent maintenant le produit et ne fichier pas la version</span><span class="sxs-lookup"><span data-stu-id="4a9a3-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="4a9a3-102">Bon nombre des API qui retournent les versions dans .NET Core retournent maintenant la version du produit plutôt que la version de fichier.</span><span class="sxs-lookup"><span data-stu-id="4a9a3-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a9a3-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="4a9a3-103">Change description</span></span>

<span data-ttu-id="4a9a3-104">Dans .NET Core 2.2 et les <xref:System.Environment.Version?displayProperty=nameWithType>versions précédentes, les méthodes telles que , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>et les propriétés de fichier dialogue pour les assemblages .NET Core reflètent la version de fichier.</span><span class="sxs-lookup"><span data-stu-id="4a9a3-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="4a9a3-105">En commençant par .NET Core 3.0, ils reflètent la version du produit.</span><span class="sxs-lookup"><span data-stu-id="4a9a3-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="4a9a3-106">Le chiffre suivant illustre la différence d’informations de version pour *l’assemblage System.Runtime.dll* pour .NET Core 2.2 (à gauche) et .NET Core 3.0 (à droite) tel qu’affiché par le dialogue des propriétés de fichiers **Windows Explorer.**</span><span class="sxs-lookup"><span data-stu-id="4a9a3-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="4a9a3-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4a9a3-108">Version introduced</span></span>

<span data-ttu-id="4a9a3-109">3.0</span><span class="sxs-lookup"><span data-stu-id="4a9a3-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a9a3-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4a9a3-110">Recommended action</span></span>

<span data-ttu-id="4a9a3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4a9a3-111">None.</span></span> <span data-ttu-id="4a9a3-112">Ce changement devrait rendre la détection de version intuitive plutôt que obtus.</span><span class="sxs-lookup"><span data-stu-id="4a9a3-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="4a9a3-113">Category</span><span class="sxs-lookup"><span data-stu-id="4a9a3-113">Category</span></span>

<span data-ttu-id="4a9a3-114">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="4a9a3-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a9a3-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="4a9a3-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
