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
ms.openlocfilehash: b32e8f0b03ef6d550c384f3d932cc295a7270028
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007661"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="45d24-102">CorMethodImpl, énumération</span><span class="sxs-lookup"><span data-stu-id="45d24-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="45d24-103">Contient des valeurs qui décrivent les fonctionnalités d’implémentation d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="45d24-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45d24-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="45d24-105">Membres</span><span class="sxs-lookup"><span data-stu-id="45d24-105">Members</span></span>  
  
|<span data-ttu-id="45d24-106">Membre</span><span class="sxs-lookup"><span data-stu-id="45d24-106">Member</span></span>|<span data-ttu-id="45d24-107">Description</span><span class="sxs-lookup"><span data-stu-id="45d24-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="45d24-108">Indicateurs qui décrivent le type de code.</span><span class="sxs-lookup"><span data-stu-id="45d24-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="45d24-109">Spécifie que l’implémentation de la méthode est en langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="45d24-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="45d24-110">Spécifie que l’implémentation de la méthode est native.</span><span class="sxs-lookup"><span data-stu-id="45d24-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="45d24-111">Spécifie que l’implémentation de la méthode est OPTI.</span><span class="sxs-lookup"><span data-stu-id="45d24-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="45d24-112">Spécifie que l’implémentation de la méthode est fournie par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="45d24-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="45d24-113">Indicateurs qui indiquent si le code est managé ou non managé.</span><span class="sxs-lookup"><span data-stu-id="45d24-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="45d24-114">Spécifie que l’implémentation de la méthode n’est pas gérée.</span><span class="sxs-lookup"><span data-stu-id="45d24-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="45d24-115">Spécifie que l’implémentation de la méthode est managée.</span><span class="sxs-lookup"><span data-stu-id="45d24-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="45d24-116">Spécifie que la méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="45d24-116">Specifies that the method is defined.</span></span> <span data-ttu-id="45d24-117">Cet indicateur est principalement utilisé dans les scénarios de fusion.</span><span class="sxs-lookup"><span data-stu-id="45d24-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="45d24-118">Spécifie que la signature de la méthode ne peut pas être tronquée pour une conversion HRESULT.</span><span class="sxs-lookup"><span data-stu-id="45d24-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="45d24-119">Réservé à un usage interne par la common language runtime.</span><span class="sxs-lookup"><span data-stu-id="45d24-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="45d24-120">Spécifie que la méthode est à thread unique par le biais de son corps.</span><span class="sxs-lookup"><span data-stu-id="45d24-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="45d24-121">Spécifie que la méthode ne peut pas être inline.</span><span class="sxs-lookup"><span data-stu-id="45d24-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="45d24-122">Spécifie que la méthode doit être inline si possible.</span><span class="sxs-lookup"><span data-stu-id="45d24-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="45d24-123">Spécifie que la méthode ne doit pas être optimisée.</span><span class="sxs-lookup"><span data-stu-id="45d24-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="45d24-124">Valeur maximale valide pour `CorMethodImpl` .</span><span class="sxs-lookup"><span data-stu-id="45d24-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45d24-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45d24-125">Requirements</span></span>  
 <span data-ttu-id="45d24-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d24-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d24-127">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="45d24-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="45d24-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d24-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d24-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45d24-129">See also</span></span>

- [<span data-ttu-id="45d24-130">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="45d24-130">Metadata Enumerations</span></span>](metadata-enumerations.md)
