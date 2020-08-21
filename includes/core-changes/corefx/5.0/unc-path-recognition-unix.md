---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720186"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="eab07-101">Reconnaissance d’URI de chemins d’accès UNC sur UNIX</span><span class="sxs-lookup"><span data-stu-id="eab07-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="eab07-102">La <xref:System.Uri> classe reconnaît maintenant les chaînes qui commencent par deux barres obliques ( `//` ) en tant que chemins d’accès UNC (Universal Naming Convention) sur les systèmes d’exploitation UNIX.</span><span class="sxs-lookup"><span data-stu-id="eab07-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="eab07-103">Cette modification rend le comportement de ces chaînes cohérent sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="eab07-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eab07-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="eab07-104">Change description</span></span>

<span data-ttu-id="eab07-105">Dans les versions précédentes de .NET, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par avec deux barres obliques, par exemple, `//contoso` sous la forme de chemins de fichiers absolus sur les systèmes d’exploitation UNIX.</span><span class="sxs-lookup"><span data-stu-id="eab07-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="eab07-106">Toutefois, sous Windows, ces chaînes sont reconnues comme des chemins d’accès UNC.</span><span class="sxs-lookup"><span data-stu-id="eab07-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="eab07-107">À compter de .NET 5,0, la <xref:System.Uri> classe reconnaît les chaînes qui commencent par avec deux barres obliques comme chemins d’accès UNC sur toutes les plateformes, y compris UNIX.</span><span class="sxs-lookup"><span data-stu-id="eab07-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="eab07-108">En outre, les propriétés se comportent selon la sémantique UNC :</span><span class="sxs-lookup"><span data-stu-id="eab07-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="eab07-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="eab07-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="eab07-110">Les barres obliques inverses dans le chemin d’accès sont remplacées par des barres obliques.</span><span class="sxs-lookup"><span data-stu-id="eab07-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="eab07-111">Par exemple, `//first\second` devient `//first/second`.</span><span class="sxs-lookup"><span data-stu-id="eab07-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="eab07-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> n’encode pas les caractères en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="eab07-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="eab07-113">Par exemple, `//first/\uFFF0` n’est *pas* converti en `//first/%EF%BF%B0` .</span><span class="sxs-lookup"><span data-stu-id="eab07-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eab07-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="eab07-114">Version introduced</span></span>

<span data-ttu-id="eab07-115">5,0</span><span class="sxs-lookup"><span data-stu-id="eab07-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eab07-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="eab07-116">Recommended action</span></span>

<span data-ttu-id="eab07-117">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="eab07-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="eab07-118">Category</span><span class="sxs-lookup"><span data-stu-id="eab07-118">Category</span></span>

<span data-ttu-id="eab07-119">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="eab07-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eab07-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="eab07-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
