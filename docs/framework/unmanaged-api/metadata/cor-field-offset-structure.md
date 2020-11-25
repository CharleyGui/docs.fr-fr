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
ms.openlocfilehash: 1a8ab5aa5909af60089d5e4cc8092e15bc75e8cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724180"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="903e5-102">COR_FIELD_OFFSET, structure</span><span class="sxs-lookup"><span data-stu-id="903e5-102">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="903e5-103">Stocke l'offset, dans une classe, du champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="903e5-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="903e5-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="903e5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="903e5-105">Members</span></span>  
  
|<span data-ttu-id="903e5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="903e5-106">Member</span></span>|<span data-ttu-id="903e5-107">Description</span><span class="sxs-lookup"><span data-stu-id="903e5-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="903e5-108">`mdFieldDef`Jeton de métadonnées qui représente le champ.</span><span class="sxs-lookup"><span data-stu-id="903e5-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="903e5-109">Offset du champ dans sa classe.</span><span class="sxs-lookup"><span data-stu-id="903e5-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="903e5-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="903e5-110">Remarks</span></span>  

 <span data-ttu-id="903e5-111">Les méthodes [IMetaDataImport :: GetClassLayout](imetadataimport-getclasslayout-method.md) et [IMetaDataEmit :: SetClassLayout,](imetadataemit-setclasslayout-method.md) prennent un paramètre de type `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="903e5-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="903e5-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="903e5-112">Requirements</span></span>  

 <span data-ttu-id="903e5-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="903e5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="903e5-114">**En-tête :** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="903e5-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="903e5-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="903e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903e5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="903e5-116">See also</span></span>

- [<span data-ttu-id="903e5-117">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="903e5-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="903e5-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="903e5-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="903e5-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="903e5-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
