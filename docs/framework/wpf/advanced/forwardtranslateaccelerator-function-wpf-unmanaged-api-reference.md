---
title: Fonction ForwardTranslateAccelerator - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186632"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d50fe-102">Fonction ForwardTranslateAccelerator (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="d50fe-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d50fe-103">Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="d50fe-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d50fe-104">Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="d50fe-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50fe-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d50fe-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d50fe-106">Parameters</span></span>  
 <span data-ttu-id="d50fe-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="d50fe-107">pMsg</span></span>  
 <span data-ttu-id="d50fe-108">Un pointeur à un message.</span><span class="sxs-lookup"><span data-stu-id="d50fe-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="d50fe-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="d50fe-109">appUnhandled</span></span>  
 <span data-ttu-id="d50fe-110">`true`lorsque l’application a déjà eu la chance de gérer le message d’entrée, mais ne l’a pas géré; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="d50fe-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50fe-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d50fe-111">Requirements</span></span>  
 <span data-ttu-id="d50fe-112">**Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d50fe-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50fe-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="d50fe-113">**DLL:**</span></span>  
  
 <span data-ttu-id="d50fe-114">Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="d50fe-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d50fe-115">Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="d50fe-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d50fe-116">**Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50fe-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50fe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d50fe-117">See also</span></span>

- [<span data-ttu-id="d50fe-118">Informations de référence sur les API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="d50fe-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
