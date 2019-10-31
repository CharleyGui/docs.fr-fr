---
title: CLRDataEnumMemoryFlags, énumération
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
ms.openlocfilehash: 769e63ac6e23ae0264b79a1cd8d6e3cc1ac5a744
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132410"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="32d51-102">CLRDataEnumMemoryFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="32d51-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="32d51-103">Indique les régions de mémoire qu’un appel à la méthode [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) doit inclure.</span><span class="sxs-lookup"><span data-stu-id="32d51-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32d51-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="32d51-105">Membres</span><span class="sxs-lookup"><span data-stu-id="32d51-105">Members</span></span>  
  
|<span data-ttu-id="32d51-106">Membre</span><span class="sxs-lookup"><span data-stu-id="32d51-106">Member</span></span>|<span data-ttu-id="32d51-107">Description</span><span class="sxs-lookup"><span data-stu-id="32d51-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="32d51-108">Minidump, autrement dit, une image mémoire éparse.</span><span class="sxs-lookup"><span data-stu-id="32d51-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="32d51-109">Vidage du tas complet.</span><span class="sxs-lookup"><span data-stu-id="32d51-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32d51-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="32d51-110">Requirements</span></span>  
 <span data-ttu-id="32d51-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32d51-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32d51-112">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="32d51-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="32d51-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32d51-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32d51-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32d51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d51-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32d51-115">See also</span></span>

- [<span data-ttu-id="32d51-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="32d51-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
