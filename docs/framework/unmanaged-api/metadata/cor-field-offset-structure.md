---
title: COR_FIELD_OFFSET, structure
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443963"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="8ee05-102">COR_FIELD_OFFSET, structure</span><span class="sxs-lookup"><span data-stu-id="8ee05-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="8ee05-103">Stocke l'offset, dans une classe, du champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="8ee05-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ee05-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="8ee05-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8ee05-105">Members</span></span>  
  
|<span data-ttu-id="8ee05-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8ee05-106">Member</span></span>|<span data-ttu-id="8ee05-107">Description</span><span class="sxs-lookup"><span data-stu-id="8ee05-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="8ee05-108">An `mdFieldDef` metadata token that represents the field.</span><span class="sxs-lookup"><span data-stu-id="8ee05-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="8ee05-109">The field's offset within its class.</span><span class="sxs-lookup"><span data-stu-id="8ee05-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee05-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8ee05-110">Remarks</span></span>  
 <span data-ttu-id="8ee05-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="8ee05-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee05-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="8ee05-112">Requirements</span></span>  
 <span data-ttu-id="8ee05-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee05-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee05-114">**Header:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="8ee05-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="8ee05-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee05-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ee05-116">See also</span></span>

- [<span data-ttu-id="8ee05-117">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8ee05-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="8ee05-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8ee05-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8ee05-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8ee05-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
