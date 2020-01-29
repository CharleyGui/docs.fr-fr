---
title: Fonction Activate-référence des API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734515"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="95f6d-102">Activate, fonction (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="95f6d-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="95f6d-103">Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="95f6d-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="95f6d-104">Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="95f6d-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="95f6d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95f6d-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="95f6d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="95f6d-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="95f6d-107">Pointeur vers les paramètres d’activation de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="95f6d-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="95f6d-108">Pointeur vers l’adresse d’une mémoire tampon à un seul élément qui contient un pointeur vers un objet <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.</span><span class="sxs-lookup"><span data-stu-id="95f6d-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="95f6d-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="95f6d-109">Requirements</span></span>

<span data-ttu-id="95f6d-110">**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95f6d-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="95f6d-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="95f6d-111">**DLL:**</span></span>

<span data-ttu-id="95f6d-112">Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="95f6d-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="95f6d-113">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="95f6d-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="95f6d-114">**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95f6d-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="95f6d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95f6d-115">See also</span></span>

- [<span data-ttu-id="95f6d-116">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="95f6d-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
