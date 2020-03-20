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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176537"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="f7e52-102">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="f7e52-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="f7e52-103">Crée une instance du type géré spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7e52-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="f7e52-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="f7e52-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="f7e52-105">Utilisez l’activation COM pour créer une instance du type géré, ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées dans le cadre .NET 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="f7e52-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e52-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e52-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e52-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7e52-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="f7e52-108">[dans] Un pointeur sur le nom du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="f7e52-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="f7e52-109">[dans] Le `IID` type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="f7e52-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f7e52-110">[out] Un pointeur à un pointeur à une instance du type géré qui a été demandé par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="f7e52-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7e52-111">Notes </span><span class="sxs-lookup"><span data-stu-id="f7e52-111">Remarks</span></span>  
 <span data-ttu-id="f7e52-112">L’heure d’exécution de langue commune devrait déjà être chargée dans un processus.</span><span class="sxs-lookup"><span data-stu-id="f7e52-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="f7e52-113">Par exemple, il peut être chargé en utilisant un appel à `ClrCreateManagedInstance` la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) avant que la fonction ne soit appelée.</span><span class="sxs-lookup"><span data-stu-id="f7e52-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="f7e52-114">Si le temps d’exécution n’est pas chargé, `ClrCreateManagedInstance` tente d’abord de charger v1.0.3705 du temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7e52-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="f7e52-115">Si cela échoue, il tente de charger la dernière version de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7e52-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e52-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7e52-116">Requirements</span></span>  
 <span data-ttu-id="f7e52-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e52-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e52-118">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="f7e52-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7e52-119">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="f7e52-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7e52-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e52-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e52-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e52-121">See also</span></span>

- [<span data-ttu-id="f7e52-122">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="f7e52-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="f7e52-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="f7e52-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
