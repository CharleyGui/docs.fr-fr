---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344870"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="c4e2d-101">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="c4e2d-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="c4e2d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a la valeur par défaut `false` sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="c4e2d-103">Sur .NET Framework, sa valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4e2d-104">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="c4e2d-104">Change description</span></span>

<span data-ttu-id="c4e2d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> vous permet de lancer directement une application, par exemple, avec du code tel que `Process.Start("mspaint.exe")` qui lance Paint.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="c4e2d-106">Elle vous permet également de lancer indirectement une application associée si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="c4e2d-107">Sur .NET Framework, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true`, ce qui signifie que le code comme `Process.Start("mytextfile.txt")` lancerait le bloc-notes, si vous avez associé des fichiers *. txt* à cet éditeur.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="c4e2d-108">Pour empêcher le lancement indirect d’une application sur .NET Framework, vous devez définir explicitement <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> sur `false`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c4e2d-109">Sur .NET Core, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="c4e2d-110">Cela signifie que, par défaut, les applications associées ne sont pas lancées lorsque vous appelez `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="c4e2d-111">Cette modification a été introduite dans .NET Core pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="c4e2d-112">En général, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="c4e2d-113">Le lancement d’une application directement n’a pas besoin d’impliquer l’interpréteur de commandes Windows et de supporter les coûts de performances associés.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="c4e2d-114">Pour que ce cas par défaut soit plus rapide, .NET Core modifie la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> en `false`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c4e2d-115">Vous pouvez choisir le chemin le plus lent si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4e2d-116">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c4e2d-116">Version introduced</span></span>

<span data-ttu-id="c4e2d-117">2.1</span><span class="sxs-lookup"><span data-stu-id="c4e2d-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="c4e2d-118">Dans les versions antérieures de .NET Core, `UseShellExecute` n’était pas implémenté pour Windows.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4e2d-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c4e2d-119">Recommended action</span></span>

<span data-ttu-id="c4e2d-120">Si votre application s’appuie sur l’ancien comportement, appelez <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> avec <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> défini sur `true` sur l’objet <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="c4e2d-121">Catégorie</span><span class="sxs-lookup"><span data-stu-id="c4e2d-121">Category</span></span>

<span data-ttu-id="c4e2d-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c4e2d-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4e2d-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="c4e2d-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
