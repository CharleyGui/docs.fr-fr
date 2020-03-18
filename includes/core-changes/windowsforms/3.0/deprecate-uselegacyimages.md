---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937123"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="07994-101">Commutateur de compatibilité UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="07994-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="07994-102">Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.8, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="07994-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="07994-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="07994-103">Change description</span></span>

<span data-ttu-id="07994-104">En commençant par le cadre .NET `Switch.System.Windows.Forms.UseLegacyImages` 4.8, le commutateur de compatibilité a abordé les problèmes possibles de mise à l’échelle des images dans les scénarios ClickOnce dans des environnements DPI élevés.</span><span class="sxs-lookup"><span data-stu-id="07994-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="07994-105">Lorsqu’il `true`est configuré, le commutateur permet à l’utilisateur de restaurer l’échelle d’image héritée sur les écrans DPI élevés dont l’échelle est définie à plus de 100%.</span><span class="sxs-lookup"><span data-stu-id="07994-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="07994-106">Pour plus d’informations, voir [.NET Framework 4.8 Notes de sortie](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="07994-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="07994-107">Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.UseLegacyImages` pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="07994-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="07994-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="07994-108">Version introduced</span></span>

<span data-ttu-id="07994-109">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="07994-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07994-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="07994-110">Recommended action</span></span>

<span data-ttu-id="07994-111">Retirez l’interrupteur.</span><span class="sxs-lookup"><span data-stu-id="07994-111">Remove the switch.</span></span> <span data-ttu-id="07994-112">Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="07994-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="07994-113">Category</span><span class="sxs-lookup"><span data-stu-id="07994-113">Category</span></span>

<span data-ttu-id="07994-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07994-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07994-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="07994-115">Affected APIs</span></span>

- <span data-ttu-id="07994-116">None</span><span class="sxs-lookup"><span data-stu-id="07994-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
