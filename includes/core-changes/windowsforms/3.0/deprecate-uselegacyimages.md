---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937123"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="64eec-101">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="64eec-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="64eec-102">Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="64eec-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64eec-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="64eec-103">Change description</span></span>

<span data-ttu-id="64eec-104">À partir de la .NET Framework 4,8, `Switch.System.Windows.Forms.UseLegacyImages` le commutateur de compatibilité a résolu les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution.</span><span class="sxs-lookup"><span data-stu-id="64eec-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="64eec-105">Lorsque la valeur `true`est définie sur, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur des affichages haute résolution dont l’échelle est supérieure à 100%.</span><span class="sxs-lookup"><span data-stu-id="64eec-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="64eec-106">Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="64eec-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="64eec-107">Dans .NET Core, le `Switch.System.Windows.Forms.UseLegacyImages` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="64eec-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64eec-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="64eec-108">Version introduced</span></span>

<span data-ttu-id="64eec-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="64eec-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64eec-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="64eec-110">Recommended action</span></span>

<span data-ttu-id="64eec-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="64eec-111">Remove the switch.</span></span> <span data-ttu-id="64eec-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="64eec-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="64eec-113">Category</span><span class="sxs-lookup"><span data-stu-id="64eec-113">Category</span></span>

<span data-ttu-id="64eec-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64eec-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64eec-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="64eec-115">Affected APIs</span></span>

- <span data-ttu-id="64eec-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="64eec-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
