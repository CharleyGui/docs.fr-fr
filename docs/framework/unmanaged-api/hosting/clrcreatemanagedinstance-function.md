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
ms.openlocfilehash: 9aed79138499f1aa7b6fa3a28ad4505edd51b041
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731766"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="cf6eb-102">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="cf6eb-102">ClrCreateManagedInstance Function</span></span>

<span data-ttu-id="cf6eb-103">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="cf6eb-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="cf6eb-105">Utilisez l’activation COM pour créer une instance du type managé ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées au .NET Framework 4 et 4,5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="cf6eb-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6eb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf6eb-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf6eb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf6eb-107">Parameters</span></span>  

 `pTypeName`  
 <span data-ttu-id="cf6eb-108">dans Pointeur vers le nom du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="cf6eb-109">dans `IID` Du type d’instance demandé.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="cf6eb-110">à Pointeur vers un pointeur vers une instance du type managé qui a été demandé par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf6eb-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf6eb-111">Remarks</span></span>  

 <span data-ttu-id="cf6eb-112">Le common language runtime doit déjà être chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="cf6eb-113">Par exemple, il peut être chargé à l’aide d’un appel à la fonction [CorBindToRuntimeEx](corbindtoruntimeex-function.md) avant l’appel de la `ClrCreateManagedInstance` fonction.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="cf6eb-114">Si le runtime n’est pas chargé, `ClrCreateManagedInstance` tente d’abord de charger le v 1.0.3705 du Runtime.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="cf6eb-115">En cas d’échec, il tente de charger la version la plus récente du Runtime.</span><span class="sxs-lookup"><span data-stu-id="cf6eb-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf6eb-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf6eb-116">Requirements</span></span>  

 <span data-ttu-id="cf6eb-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf6eb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf6eb-118">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf6eb-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf6eb-119">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf6eb-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf6eb-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf6eb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6eb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf6eb-121">See also</span></span>

- [<span data-ttu-id="cf6eb-122">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="cf6eb-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="cf6eb-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="cf6eb-123">Hosting</span></span>](index.md)
