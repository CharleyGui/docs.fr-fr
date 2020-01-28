---
title: Fonction LoadFromHistory-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727925"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9d71c-102">LoadFromHistory, fonction (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="9d71c-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9d71c-103">Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="9d71c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9d71c-104">Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="9d71c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d71c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d71c-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d71c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9d71c-106">Parameters</span></span>  
 <span data-ttu-id="9d71c-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="9d71c-107">pHistoryStream</span></span>  
 <span data-ttu-id="9d71c-108">Pointeur vers un flux d’informations d’historique.</span><span class="sxs-lookup"><span data-stu-id="9d71c-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="9d71c-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="9d71c-109">pBindCtx</span></span>  
 <span data-ttu-id="9d71c-110">Pointeur vers un contexte de liaison.</span><span class="sxs-lookup"><span data-stu-id="9d71c-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d71c-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9d71c-111">Requirements</span></span>  
 <span data-ttu-id="9d71c-112">**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d71c-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d71c-113">**DLL**</span><span class="sxs-lookup"><span data-stu-id="9d71c-113">**DLL:**</span></span>  
  
 <span data-ttu-id="9d71c-114">Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="9d71c-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9d71c-115">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="9d71c-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="9d71c-116">**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d71c-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d71c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d71c-117">See also</span></span>

- [<span data-ttu-id="9d71c-118">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="9d71c-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
