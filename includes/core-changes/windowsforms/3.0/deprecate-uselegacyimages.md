---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644032"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="da664-101">Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyImages non pris en charge</span><span class="sxs-lookup"><span data-stu-id="da664-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="da664-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages`, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="da664-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="da664-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="da664-103">Change description</span></span>

<span data-ttu-id="da664-104">À partir de la .NET Framework 4,8, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages` a pris en charge les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution.</span><span class="sxs-lookup"><span data-stu-id="da664-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="da664-105">Lorsque cette option est définie sur `true`, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur les affichages à haute résolution, dont l’échelle est définie sur une valeur supérieure à 100%.</span><span class="sxs-lookup"><span data-stu-id="da664-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="da664-106">Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="da664-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="da664-107">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyImages` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="da664-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da664-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="da664-108">Version introduced</span></span>

<span data-ttu-id="da664-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="da664-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da664-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="da664-110">Recommended action</span></span>

<span data-ttu-id="da664-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="da664-111">Remove the switch.</span></span> <span data-ttu-id="da664-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="da664-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="da664-113">Category</span><span class="sxs-lookup"><span data-stu-id="da664-113">Category</span></span>

<span data-ttu-id="da664-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da664-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da664-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="da664-115">Affected APIs</span></span>

- <span data-ttu-id="da664-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="da664-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
