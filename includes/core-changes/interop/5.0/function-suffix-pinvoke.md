---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062421"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="693a3-101">Pas de détection de suffixe A/W sur les plateformes non-Windows</span><span class="sxs-lookup"><span data-stu-id="693a3-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="693a3-102">Les runtimes .NET n’ajoutent plus `A` `W` de suffixe ou pour les noms d’exportation de fonction lors de la détection pour P/Invoke sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="693a3-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="693a3-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="693a3-103">Version introduced</span></span>

<span data-ttu-id="693a3-104">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="693a3-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="693a3-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="693a3-105">Change description</span></span>

<span data-ttu-id="693a3-106">[Windows a une convention](/windows/win32/intl/conventions-for-function-prototypes) d’ajout d' `A` un `W` suffixe ou à SDK Windows noms de fonction, qui correspondent respectivement à la page de codes Windows et aux versions Unicode.</span><span class="sxs-lookup"><span data-stu-id="693a3-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="693a3-107">Dans les versions précédentes de .NET, les runtimes CoreCLR et mono ajoutaient `A` un `W` suffixe ou au nom de l’exportation lors de la détection d’exportation pour P/Invoke *sur toutes les plateformes*.</span><span class="sxs-lookup"><span data-stu-id="693a3-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="693a3-108">Dans .NET 5,0 et versions ultérieures, `A` un `W` suffixe ou est ajouté au nom d’exportation lors de la découverte de l’exportation *sur Windows uniquement*.</span><span class="sxs-lookup"><span data-stu-id="693a3-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="693a3-109">Sur les plateformes UNIX, le suffixe n’est pas ajouté.</span><span class="sxs-lookup"><span data-stu-id="693a3-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="693a3-110">La sémantique des deux runtimes sur la plate-forme Windows reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="693a3-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="693a3-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="693a3-111">Reason for change</span></span>

<span data-ttu-id="693a3-112">Cette modification a été apportée pour simplifier la détection inter-plateformes.</span><span class="sxs-lookup"><span data-stu-id="693a3-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="693a3-113">La surcharge ne doit pas être encourue, étant donné que les plateformes non-Windows ne contiennent pas cette sémantique.</span><span class="sxs-lookup"><span data-stu-id="693a3-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="693a3-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="693a3-114">Recommended action</span></span>

<span data-ttu-id="693a3-115">Pour atténuer la modification, vous pouvez ajouter manuellement le suffixe souhaité sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="693a3-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="693a3-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="693a3-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="693a3-117">Category</span><span class="sxs-lookup"><span data-stu-id="693a3-117">Category</span></span>

<span data-ttu-id="693a3-118">Interop</span><span class="sxs-lookup"><span data-stu-id="693a3-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="693a3-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="693a3-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
