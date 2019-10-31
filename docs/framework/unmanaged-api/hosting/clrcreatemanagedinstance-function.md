---
title: ClrCreateManagedInstance, fonction
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131989"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="2e7e6-102">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="2e7e6-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="2e7e6-103">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="2e7e6-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="2e7e6-105">Utilisez l’activation COM pour créer une instance du type managé ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées au .NET Framework 4 et 4,5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="2e7e6-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e7e6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e7e6-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e7e6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e7e6-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="2e7e6-108">dans Pointeur vers le nom du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="2e7e6-109">dans `IID` du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="2e7e6-110">à Pointeur vers un pointeur vers une instance du type managé qui a été demandé par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e7e6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2e7e6-111">Remarks</span></span>  
 <span data-ttu-id="2e7e6-112">Le common language runtime doit déjà être chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="2e7e6-113">Par exemple, il peut être chargé à l’aide d’un appel à la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) avant l’appel de la fonction `ClrCreateManagedInstance`.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="2e7e6-114">Si le runtime n’est pas chargé, `ClrCreateManagedInstance` essaie tout d’abord de charger le v 1.0.3705 du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="2e7e6-115">En cas d’échec, il tente de charger la version la plus récente du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2e7e6-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e7e6-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="2e7e6-116">Requirements</span></span>  
 <span data-ttu-id="2e7e6-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e7e6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e7e6-118">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e7e6-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e7e6-119">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e7e6-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e7e6-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e7e6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7e6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e7e6-121">See also</span></span>

- [<span data-ttu-id="2e7e6-122">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="2e7e6-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="2e7e6-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="2e7e6-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
