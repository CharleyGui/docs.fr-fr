---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116376"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="a8a8f-101">Types dans l’espace de noms Microsoft. VisualBasic. MyServices non disponibles</span><span class="sxs-lookup"><span data-stu-id="a8a8f-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="a8a8f-102">Les types de l’espace de noms <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="a8a8f-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8a8f-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a8a8f-103">Version introduced</span></span>

<span data-ttu-id="a8a8f-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a8a8f-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="a8a8f-105">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="a8a8f-105">Change description</span></span>

<span data-ttu-id="a8a8f-106">Les types de l’espace de noms <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> étaient disponibles dans certaines versions préliminaires de .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a8a8f-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="a8a8f-107">Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="a8a8f-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="a8a8f-108">Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a8a8f-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8a8f-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a8a8f-109">Recommended action</span></span>

<span data-ttu-id="a8a8f-110">Si votre code dépend de l’utilisation des types **Microsoft. VisualBasic. MyServices** et de leurs membres, il existe des types et des membres correspondants dans la bibliothèque de classes .net.</span><span class="sxs-lookup"><span data-stu-id="a8a8f-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="a8a8f-111">Voici un mappage des types **Microsoft. VisualBasic. MyServices** aux types de bibliothèques de classes .net équivalents :</span><span class="sxs-lookup"><span data-stu-id="a8a8f-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="a8a8f-112">Type Microsoft. VisualBasic. MyServices</span><span class="sxs-lookup"><span data-stu-id="a8a8f-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="a8a8f-113">Type de bibliothèque de classes .NET</span><span class="sxs-lookup"><span data-stu-id="a8a8f-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="a8a8f-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> pour les applications WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> pour les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8a8f-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="a8a8f-115">Types dans l’espace de noms <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="a8a8f-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="a8a8f-116">Types relatifs au registre dans l’espace de noms <xref:Microsoft.Win32></span><span class="sxs-lookup"><span data-stu-id="a8a8f-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="a8a8f-117">Catégorie</span><span class="sxs-lookup"><span data-stu-id="a8a8f-117">Category</span></span>

<span data-ttu-id="a8a8f-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8a8f-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8a8f-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a8a8f-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
