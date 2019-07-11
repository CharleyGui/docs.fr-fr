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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1ae530b8488dcd375e91058a227316dd38cf4ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779159"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="31bf9-102">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="31bf9-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="31bf9-103">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="31bf9-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="31bf9-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="31bf9-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="31bf9-105">Utiliser l’activation de COM pour créer une instance du type managé ou utilisez l’hébergement (consultez [CLR Interfaces d’hébergement ajoutées dans le .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="31bf9-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31bf9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31bf9-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31bf9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31bf9-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="31bf9-108">[in] Un pointeur vers le nom du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="31bf9-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="31bf9-109">[in] Le `IID` type de l’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="31bf9-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="31bf9-110">[out] Pointeur vers un pointeur vers une instance du type managé qui a été demandée par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="31bf9-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31bf9-111">Notes</span><span class="sxs-lookup"><span data-stu-id="31bf9-111">Remarks</span></span>  
 <span data-ttu-id="31bf9-112">Le common language runtime doit déjà être chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="31bf9-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="31bf9-113">Par exemple, il peut être chargé à l’aide d’un appel à la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonctionner avant du `ClrCreateManagedInstance` fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="31bf9-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="31bf9-114">Si le runtime n’est pas chargé, `ClrCreateManagedInstance` essaie d’abord charger v1.0.3705 du runtime.</span><span class="sxs-lookup"><span data-stu-id="31bf9-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="31bf9-115">Si cette tentative échoue, il tente de charger la dernière version du runtime.</span><span class="sxs-lookup"><span data-stu-id="31bf9-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31bf9-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31bf9-116">Requirements</span></span>  
 <span data-ttu-id="31bf9-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31bf9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31bf9-118">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31bf9-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31bf9-119">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31bf9-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31bf9-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31bf9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31bf9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31bf9-121">See also</span></span>

- [<span data-ttu-id="31bf9-122">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="31bf9-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="31bf9-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="31bf9-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
