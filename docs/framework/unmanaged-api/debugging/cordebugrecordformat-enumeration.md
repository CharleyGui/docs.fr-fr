---
title: CorDebugRecordFormat, énumération
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916472"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="79633-102">CorDebugRecordFormat, énumération</span><span class="sxs-lookup"><span data-stu-id="79633-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="79633-103">Décrit le format des données dans un tableau d'octets qui contient des informations sur un événement de débogage d'exception native.</span><span class="sxs-lookup"><span data-stu-id="79633-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79633-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79633-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="79633-105">Membres</span><span class="sxs-lookup"><span data-stu-id="79633-105">Members</span></span>  
  
|<span data-ttu-id="79633-106">Membre</span><span class="sxs-lookup"><span data-stu-id="79633-106">Member</span></span>|<span data-ttu-id="79633-107">Description</span><span class="sxs-lookup"><span data-stu-id="79633-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="79633-108">Les données correspondent à un enregistrement d'exception Windows 32 bits.</span><span class="sxs-lookup"><span data-stu-id="79633-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="79633-109">Les données correspondent à un enregistrement d'exception Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="79633-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79633-110">Notes</span><span class="sxs-lookup"><span data-stu-id="79633-110">Remarks</span></span>  
 <span data-ttu-id="79633-111">Un membre de l' `CorDebugRecordFormat` énumération est passé à la méthode [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) pour indiquer le format du tableau d’octets dans `pRecord` son argument.</span><span class="sxs-lookup"><span data-stu-id="79633-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79633-112">Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.</span><span class="sxs-lookup"><span data-stu-id="79633-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79633-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79633-113">Requirements</span></span>  
 <span data-ttu-id="79633-114">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79633-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79633-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79633-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79633-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79633-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79633-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79633-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79633-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79633-118">See also</span></span>

- [<span data-ttu-id="79633-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="79633-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
