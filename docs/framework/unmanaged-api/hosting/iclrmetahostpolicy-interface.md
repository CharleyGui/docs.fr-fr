---
title: ICLRMetaHostPolicy, interface
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703530"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="1eb1e-102">ICLRMetaHostPolicy, interface</span><span class="sxs-lookup"><span data-stu-id="1eb1e-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="1eb1e-103">Fournit la méthode [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , qui retourne un pointeur vers une interface Common Language Runtime (CLR) en fonction d’un critère de stratégie, d’un assembly managé, d’une version et d’un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-103">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1eb1e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1eb1e-104">Methods</span></span>  
  
|<span data-ttu-id="1eb1e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1eb1e-105">Method</span></span>|<span data-ttu-id="1eb1e-106">Description</span><span class="sxs-lookup"><span data-stu-id="1eb1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1eb1e-107">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1eb1e-107">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="1eb1e-108">Fournit une interface CLR par défaut basée sur un critère de stratégie, un assembly managé, une version et un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eb1e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1eb1e-109">Remarks</span></span>  
 <span data-ttu-id="1eb1e-110">Vous pouvez obtenir une référence à cette interface en appelant la fonction [CLRCreateInstance](clrcreateinstance-function.md) comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1eb1e-110">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="1eb1e-111">Cette interface ne charge pas ou n’active pas réellement le CLR, mais retourne simplement la version CLR par défaut en fonction des versions disponibles qui sont installées ou chargées.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="1eb1e-112">L’API d’hébergement .NET Framework 4 consolide les stratégies afin que les hôtes ayant des besoins spécifiques puissent utiliser les fonctionnalités de base sans engager de pénalités involontaires.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="1eb1e-113">Par exemple, la plupart des exportations de MSCorEE. dll sont liées à un CLR spécifique, bien qu’une méthode puisse ne pas l’exiger logiquement.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="1eb1e-114">L’énumération [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) fournit des stratégies de liaison communes à la majorité des hôtes.</span><span class="sxs-lookup"><span data-stu-id="1eb1e-114">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb1e-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="1eb1e-115">Requirements</span></span>  
 <span data-ttu-id="1eb1e-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb1e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb1e-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="1eb1e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1eb1e-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1eb1e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1eb1e-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb1e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1eb1e-120">See also</span></span>

- [<span data-ttu-id="1eb1e-121">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="1eb1e-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="1eb1e-122">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="1eb1e-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1eb1e-123">Hébergement</span><span class="sxs-lookup"><span data-stu-id="1eb1e-123">Hosting</span></span>](index.md)
