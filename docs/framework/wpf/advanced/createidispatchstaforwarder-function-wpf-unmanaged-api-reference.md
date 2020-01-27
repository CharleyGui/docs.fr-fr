---
title: Fonction CreateIDispatchSTAForwarder-informations de référence sur les API non managées WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738027"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1a1e5-102">CreateIDispatchSTAForwarder, fonction (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="1a1e5-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="1a1e5-103">Cette API prend en charge l’infrastructure Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="1a1e5-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="1a1e5-104">Utilisé par l’infrastructure Windows Presentation Foundation (WPF) pour la gestion des threads et de Windows.</span><span class="sxs-lookup"><span data-stu-id="1a1e5-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a1e5-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a1e5-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="1a1e5-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1a1e5-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a1e5-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="1a1e5-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="1a1e5-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="1a1e5-109">Pointeur vers une interface de `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="1a1e5-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="1a1e5-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="1a1e5-110">ppForwarder</span></span>  
 <span data-ttu-id="1a1e5-111">Pointeur vers l’adresse d’une interface de `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="1a1e5-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a1e5-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1a1e5-112">Requirements</span></span>  
 <span data-ttu-id="1a1e5-113">**Plateformes :** Consultez [.NET Framework Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1e5-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1e5-114">**DLL**</span><span class="sxs-lookup"><span data-stu-id="1a1e5-114">**DLL:**</span></span>  
  
 <span data-ttu-id="1a1e5-115">Dans les .NET Framework 3,0 et 3,5 : PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="1a1e5-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="1a1e5-116">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="1a1e5-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="1a1e5-117">**Version de .NET Framework :** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1e5-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1e5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a1e5-118">See also</span></span>

- [<span data-ttu-id="1a1e5-119">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="1a1e5-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
