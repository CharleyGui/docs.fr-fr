---
title: 'Modification avec rupture : aucune détection de suffixe/W sur les plateformes non-Windows'
description: Découvrez les modifications avec rupture d’interopérabilité dans .NET 5,0 où les suffixes ne sont plus ajoutés aux noms d’exportation de fonction lors de la détection des P/Invoke sur les plateformes non-Windows.
ms.date: 08/13/2020
ms.openlocfilehash: a4c612a81796faf80fa257df21232a54f7b95431
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761057"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="a27dd-103">Pas de détection de suffixe A/W sur les plateformes non-Windows</span><span class="sxs-lookup"><span data-stu-id="a27dd-103">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="a27dd-104">Les runtimes .NET n’ajoutent plus `A` `W` de suffixe ou pour les noms d’exportation de fonction lors de la détection pour P/Invoke sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="a27dd-104">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a27dd-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a27dd-105">Version introduced</span></span>

<span data-ttu-id="a27dd-106">5.0</span><span class="sxs-lookup"><span data-stu-id="a27dd-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="a27dd-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a27dd-107">Change description</span></span>

<span data-ttu-id="a27dd-108">[Windows a une convention](/windows/win32/intl/conventions-for-function-prototypes) d’ajout d' `A` un `W` suffixe ou à SDK Windows noms de fonction, qui correspondent respectivement à la page de codes Windows et aux versions Unicode.</span><span class="sxs-lookup"><span data-stu-id="a27dd-108">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="a27dd-109">Dans les versions précédentes de .NET, les runtimes CoreCLR et mono ajoutaient `A` un `W` suffixe ou au nom de l’exportation lors de la détection d’exportation pour P/Invoke *sur toutes les plateformes*.</span><span class="sxs-lookup"><span data-stu-id="a27dd-109">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="a27dd-110">Dans .NET 5,0 et versions ultérieures, `A` un `W` suffixe ou est ajouté au nom d’exportation lors de la découverte de l’exportation *sur Windows uniquement*.</span><span class="sxs-lookup"><span data-stu-id="a27dd-110">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="a27dd-111">Sur les plateformes UNIX, le suffixe n’est pas ajouté.</span><span class="sxs-lookup"><span data-stu-id="a27dd-111">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="a27dd-112">La sémantique des deux runtimes sur la plate-forme Windows reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="a27dd-112">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a27dd-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a27dd-113">Reason for change</span></span>

<span data-ttu-id="a27dd-114">Cette modification a été apportée pour simplifier la détection inter-plateformes.</span><span class="sxs-lookup"><span data-stu-id="a27dd-114">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="a27dd-115">La surcharge ne doit pas être encourue, étant donné que les plateformes non-Windows ne contiennent pas cette sémantique.</span><span class="sxs-lookup"><span data-stu-id="a27dd-115">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a27dd-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a27dd-116">Recommended action</span></span>

<span data-ttu-id="a27dd-117">Pour atténuer la modification, vous pouvez ajouter manuellement le suffixe souhaité sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="a27dd-117">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="a27dd-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a27dd-118">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a><span data-ttu-id="a27dd-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a27dd-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
