---
title: CorPEKind, énumération
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 74670a1477546066145bd4bbf2f123a252e10b55
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436471"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="af1c9-102">CorPEKind, énumération</span><span class="sxs-lookup"><span data-stu-id="af1c9-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="af1c9-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="af1c9-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af1c9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="af1c9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="af1c9-105">Members</span></span>  
  
|<span data-ttu-id="af1c9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="af1c9-106">Member</span></span>|<span data-ttu-id="af1c9-107">Description</span><span class="sxs-lookup"><span data-stu-id="af1c9-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="af1c9-108">Indicates that this is not a PE file.</span><span class="sxs-lookup"><span data-stu-id="af1c9-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="af1c9-109">Indicates that this PE file contains only managed code.</span><span class="sxs-lookup"><span data-stu-id="af1c9-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="af1c9-110">Indicates that this PE file makes Win32 calls.</span><span class="sxs-lookup"><span data-stu-id="af1c9-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="af1c9-111">Indicates that this PE file runs on a 64-bit platform.</span><span class="sxs-lookup"><span data-stu-id="af1c9-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="af1c9-112">Indicates that this PE file is native code.</span><span class="sxs-lookup"><span data-stu-id="af1c9-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="af1c9-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="af1c9-113">pe32BitPreferred</span></span>|<span data-ttu-id="af1c9-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span><span class="sxs-lookup"><span data-stu-id="af1c9-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af1c9-115">Notes</span><span class="sxs-lookup"><span data-stu-id="af1c9-115">Remarks</span></span>  
 <span data-ttu-id="af1c9-116">These values can be used in bitwise combinations.</span><span class="sxs-lookup"><span data-stu-id="af1c9-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1c9-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="af1c9-117">Requirements</span></span>  
 <span data-ttu-id="af1c9-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af1c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af1c9-119">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="af1c9-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="af1c9-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af1c9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1c9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af1c9-121">See also</span></span>

- [<span data-ttu-id="af1c9-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="af1c9-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
