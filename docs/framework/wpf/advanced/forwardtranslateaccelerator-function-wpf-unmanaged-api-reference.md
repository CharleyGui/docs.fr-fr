---
title: Fonction ForwardTranslateAccelerator-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747036"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ab04e-102">ForwardTranslateAccelerator, fonction (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="ab04e-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ab04e-103">Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="ab04e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ab04e-104">Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="ab04e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab04e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab04e-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab04e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab04e-106">Parameters</span></span>  
 <span data-ttu-id="ab04e-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="ab04e-107">pMsg</span></span>  
 <span data-ttu-id="ab04e-108">Pointeur vers un message.</span><span class="sxs-lookup"><span data-stu-id="ab04e-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="ab04e-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="ab04e-109">appUnhandled</span></span>  
 <span data-ttu-id="ab04e-110">`true` lorsque l’application a déjà eu la possibilité de gérer le message d’entrée, mais ne l’a pas gérée ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab04e-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab04e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab04e-111">Requirements</span></span>  
 <span data-ttu-id="ab04e-112">**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab04e-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab04e-113">**DLL**</span><span class="sxs-lookup"><span data-stu-id="ab04e-113">**DLL:**</span></span>  
  
 <span data-ttu-id="ab04e-114">Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="ab04e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ab04e-115">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="ab04e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ab04e-116">**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab04e-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab04e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab04e-117">See also</span></span>

- [<span data-ttu-id="ab04e-118">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="ab04e-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
