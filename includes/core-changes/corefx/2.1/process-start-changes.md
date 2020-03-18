---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449393"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="034b7-101">Variation de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="034b7-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="034b7-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>a une valeur `false` par défaut de sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="034b7-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="034b7-103">Sur .NET Framework, sa `true`valeur par défaut est .</span><span class="sxs-lookup"><span data-stu-id="034b7-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="034b7-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="034b7-104">Change description</span></span>

<span data-ttu-id="034b7-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>vous permet de lancer une application directement, `Process.Start("mspaint.exe")` par exemple, avec un code comme celui lance Paint.</span><span class="sxs-lookup"><span data-stu-id="034b7-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="034b7-106">Il vous permet également de lancer <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> indirectement une `true`application associée si elle est configuré à .</span><span class="sxs-lookup"><span data-stu-id="034b7-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="034b7-107">Sur .NET Framework, la <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`valeur par défaut `Process.Start("mytextfile.txt")` pour est , ce qui signifie que le code tel serait lancer Notepad, si vous avez associé des fichiers *.txt* avec cet éditeur.</span><span class="sxs-lookup"><span data-stu-id="034b7-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="034b7-108">Pour éviter de lancer indirectement une application sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> .NET Framework, vous devez définir explicitement à `false`.</span><span class="sxs-lookup"><span data-stu-id="034b7-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="034b7-109">Sur .NET Core, la <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`valeur par défaut pour est .</span><span class="sxs-lookup"><span data-stu-id="034b7-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="034b7-110">Cela signifie que, par défaut, les applications `Process.Start`associées ne sont pas lancées lorsque vous appelez .</span><span class="sxs-lookup"><span data-stu-id="034b7-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="034b7-111">Ce changement a été introduit dans .NET Core pour des raisons de performance.</span><span class="sxs-lookup"><span data-stu-id="034b7-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="034b7-112">Typiquement, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement.</span><span class="sxs-lookup"><span data-stu-id="034b7-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="034b7-113">Le lancement direct d’une application n’a pas besoin d’impliquer la coque Windows et d’engager le coût de performance associé.</span><span class="sxs-lookup"><span data-stu-id="034b7-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="034b7-114">Pour rendre ce cas par défaut plus rapide, .NET Core change la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`.</span><span class="sxs-lookup"><span data-stu-id="034b7-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="034b7-115">Vous pouvez opter pour le chemin plus lent si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="034b7-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="034b7-116">Version introduite</span><span class="sxs-lookup"><span data-stu-id="034b7-116">Version introduced</span></span>

<span data-ttu-id="034b7-117">2.1</span><span class="sxs-lookup"><span data-stu-id="034b7-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="034b7-118">Dans les versions précédentes `UseShellExecute` de .NET Core, n’a pas été implémenté pour Windows.</span><span class="sxs-lookup"><span data-stu-id="034b7-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="034b7-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="034b7-119">Recommended action</span></span>

<span data-ttu-id="034b7-120">Si votre application s’appuie <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> l’ancien comportement, appelez avec défini `true` sur l’objet. <xref:System.Diagnostics.ProcessStartInfo></span><span class="sxs-lookup"><span data-stu-id="034b7-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="034b7-121">Category</span><span class="sxs-lookup"><span data-stu-id="034b7-121">Category</span></span>

<span data-ttu-id="034b7-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="034b7-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="034b7-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="034b7-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
