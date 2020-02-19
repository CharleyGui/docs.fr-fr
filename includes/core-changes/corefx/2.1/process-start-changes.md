---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449393"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="c5d1b-101">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="c5d1b-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="c5d1b-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a la valeur par défaut `false` sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="c5d1b-103">Sur .NET Framework, sa valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c5d1b-104">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="c5d1b-104">Change description</span></span>

<span data-ttu-id="c5d1b-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> vous permet de lancer directement une application, par exemple, avec du code tel que `Process.Start("mspaint.exe")` qui lance Paint.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="c5d1b-106">Elle vous permet également de lancer indirectement une application associée si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="c5d1b-107">Sur .NET Framework, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true`, ce qui signifie que le code comme `Process.Start("mytextfile.txt")` lancerait le bloc-notes, si vous avez associé des fichiers *. txt* à cet éditeur.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="c5d1b-108">Pour empêcher le lancement indirect d’une application sur .NET Framework, vous devez définir explicitement <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> sur `false`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c5d1b-109">Sur .NET Core, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="c5d1b-110">Cela signifie que, par défaut, les applications associées ne sont pas lancées lorsque vous appelez `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="c5d1b-111">Cette modification a été introduite dans .NET Core pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="c5d1b-112">En général, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="c5d1b-113">Le lancement d’une application directement n’a pas besoin d’impliquer l’interpréteur de commandes Windows et de supporter les coûts de performances associés.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="c5d1b-114">Pour que ce cas par défaut soit plus rapide, .NET Core modifie la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> en `false`.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c5d1b-115">Vous pouvez choisir le chemin le plus lent si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5d1b-116">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c5d1b-116">Version introduced</span></span>

<span data-ttu-id="c5d1b-117">2.1</span><span class="sxs-lookup"><span data-stu-id="c5d1b-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="c5d1b-118">Dans les versions antérieures de .NET Core, `UseShellExecute` n’était pas implémenté pour Windows.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5d1b-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c5d1b-119">Recommended action</span></span>

<span data-ttu-id="c5d1b-120">Si votre application s’appuie sur l’ancien comportement, appelez <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> avec <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> défini sur `true` sur l’objet <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="c5d1b-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="c5d1b-121">Category</span><span class="sxs-lookup"><span data-stu-id="c5d1b-121">Category</span></span>

<span data-ttu-id="c5d1b-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c5d1b-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5d1b-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="c5d1b-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
