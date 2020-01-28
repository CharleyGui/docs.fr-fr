---
title: Fonction ProcessUnhandledException-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743922"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="81331-102">ProcessUnhandledException, fonction (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="81331-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="81331-103">Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="81331-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="81331-104">Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="81331-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81331-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81331-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="81331-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="81331-106">Parameters</span></span>  
 <span data-ttu-id="81331-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="81331-107">errorMsg</span></span>  
 <span data-ttu-id="81331-108">Message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="81331-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81331-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="81331-109">Requirements</span></span>  
 <span data-ttu-id="81331-110">**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81331-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81331-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="81331-111">**DLL:**</span></span>  
  
 <span data-ttu-id="81331-112">Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="81331-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="81331-113">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="81331-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="81331-114">**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81331-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81331-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81331-115">See also</span></span>

- [<span data-ttu-id="81331-116">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="81331-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
