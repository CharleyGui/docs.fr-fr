---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911555"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="c405a-101">Modification de la valeur par défaut de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="c405a-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="c405a-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a une valeur par défaut de `false` sur .net core.</span><span class="sxs-lookup"><span data-stu-id="c405a-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="c405a-103">Sur .NET Framework, sa valeur par défaut est `true` .</span><span class="sxs-lookup"><span data-stu-id="c405a-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c405a-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c405a-104">Change description</span></span>

<span data-ttu-id="c405a-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> vous permet de lancer une application directement, par exemple avec un code tel que `Process.Start("mspaint.exe")` qui lance Paint.</span><span class="sxs-lookup"><span data-stu-id="c405a-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="c405a-106">Elle vous permet également de lancer indirectement une application associée si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="c405a-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="c405a-107">Sur .NET Framework, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true` , ce qui signifie que le code `Process.Start("mytextfile.txt")` peut lancer le bloc-notes, si vous avez associé des fichiers *. txt* à cet éditeur.</span><span class="sxs-lookup"><span data-stu-id="c405a-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="c405a-108">Pour empêcher le lancement indirect d’une application sur .NET Framework, vous devez définir explicitement sur <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="c405a-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c405a-109">Sur .NET Core, la valeur par défaut de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `false` .</span><span class="sxs-lookup"><span data-stu-id="c405a-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="c405a-110">Cela signifie que, par défaut, les applications associées ne sont pas lancées lorsque vous appelez `Process.Start` .</span><span class="sxs-lookup"><span data-stu-id="c405a-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="c405a-111">Les propriétés suivantes sur <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> ne sont fonctionnelles que si <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> est `true` :</span><span class="sxs-lookup"><span data-stu-id="c405a-111">The following properties on <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> are only functional when <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`:</span></span>

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <span data-ttu-id="c405a-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c405a-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c405a-113">Cette modification a été introduite dans .NET Core pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="c405a-113">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="c405a-114">En général, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> est utilisé pour lancer une application directement.</span><span class="sxs-lookup"><span data-stu-id="c405a-114">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="c405a-115">Le lancement d’une application directement n’a pas besoin d’impliquer l’interpréteur de commandes Windows et de supporter les coûts de performances associés.</span><span class="sxs-lookup"><span data-stu-id="c405a-115">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="c405a-116">Pour que ce cas par défaut soit plus rapide, .NET Core remplace la valeur par défaut par <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` .</span><span class="sxs-lookup"><span data-stu-id="c405a-116">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c405a-117">Vous pouvez choisir le chemin le plus lent si vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="c405a-117">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c405a-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c405a-118">Version introduced</span></span>

<span data-ttu-id="c405a-119">2.1</span><span class="sxs-lookup"><span data-stu-id="c405a-119">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="c405a-120">Dans les versions antérieures de .NET Core, `UseShellExecute` n’était pas implémenté pour Windows.</span><span class="sxs-lookup"><span data-stu-id="c405a-120">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c405a-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c405a-121">Recommended action</span></span>

<span data-ttu-id="c405a-122">Si votre application s’appuie sur l’ancien comportement, appelez <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> avec <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> défini sur `true` sur l' <xref:System.Diagnostics.ProcessStartInfo> objet.</span><span class="sxs-lookup"><span data-stu-id="c405a-122">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="c405a-123">Category</span><span class="sxs-lookup"><span data-stu-id="c405a-123">Category</span></span>

<span data-ttu-id="c405a-124">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="c405a-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c405a-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="c405a-125">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
