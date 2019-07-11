---
title: CorMethodImpl, énumération
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c88c12646a13e5a24f2475bd2db04c8c831141c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781764"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="59068-102">CorMethodImpl, énumération</span><span class="sxs-lookup"><span data-stu-id="59068-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="59068-103">Contient des valeurs qui décrivent les fonctionnalités d’implémentation d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="59068-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59068-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="59068-105">Membres</span><span class="sxs-lookup"><span data-stu-id="59068-105">Members</span></span>  
  
|<span data-ttu-id="59068-106">Membre</span><span class="sxs-lookup"><span data-stu-id="59068-106">Member</span></span>|<span data-ttu-id="59068-107">Description</span><span class="sxs-lookup"><span data-stu-id="59068-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="59068-108">Indicateurs qui décrivent le type de code.</span><span class="sxs-lookup"><span data-stu-id="59068-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="59068-109">Spécifie que l’implémentation de méthode est Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="59068-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="59068-110">Spécifie que l’implémentation de la méthode est native.</span><span class="sxs-lookup"><span data-stu-id="59068-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="59068-111">Spécifie que l’implémentation de méthode est OPTIL.</span><span class="sxs-lookup"><span data-stu-id="59068-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="59068-112">Spécifie que l’implémentation de méthode est fournie par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="59068-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="59068-113">Indicateurs qui indiquent si le code est géré ou non géré.</span><span class="sxs-lookup"><span data-stu-id="59068-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="59068-114">Spécifie que l’implémentation de méthode n’est pas gérée.</span><span class="sxs-lookup"><span data-stu-id="59068-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="59068-115">Spécifie que l’implémentation de méthode est gérée.</span><span class="sxs-lookup"><span data-stu-id="59068-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="59068-116">Spécifie que la méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="59068-116">Specifies that the method is defined.</span></span> <span data-ttu-id="59068-117">Cet indicateur est utilisé principalement dans les scénarios de fusion.</span><span class="sxs-lookup"><span data-stu-id="59068-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="59068-118">Spécifie que la signature de méthode ne peut pas être tronquée pour une conversion HRESULT.</span><span class="sxs-lookup"><span data-stu-id="59068-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="59068-119">Réservé à un usage interne par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="59068-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="59068-120">Spécifie que la méthode est à thread unique son corps.</span><span class="sxs-lookup"><span data-stu-id="59068-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="59068-121">Spécifie que la méthode ne peut pas être inline.</span><span class="sxs-lookup"><span data-stu-id="59068-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="59068-122">Spécifie que la méthode doit être inline si possible.</span><span class="sxs-lookup"><span data-stu-id="59068-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="59068-123">Spécifie que la méthode ne doit pas être optimisée.</span><span class="sxs-lookup"><span data-stu-id="59068-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="59068-124">La valeur valide maximale pour un `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="59068-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59068-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59068-125">Requirements</span></span>  
 <span data-ttu-id="59068-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59068-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59068-127">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="59068-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="59068-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59068-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59068-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59068-129">See also</span></span>

- [<span data-ttu-id="59068-130">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="59068-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
