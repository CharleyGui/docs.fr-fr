---
title: COR_FIELD, structure
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f857f773f02da25fe6650000be777b8290f5af91
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274059"
---
# <a name="cor_field-structure"></a><span data-ttu-id="961f9-102">COR_FIELD, structure</span><span class="sxs-lookup"><span data-stu-id="961f9-102">COR_FIELD Structure</span></span>
<span data-ttu-id="961f9-103">Fournit des informations sur un champ dans un objet.</span><span class="sxs-lookup"><span data-stu-id="961f9-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="961f9-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="961f9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="961f9-105">Members</span></span>  
  
|<span data-ttu-id="961f9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="961f9-106">Member</span></span>|<span data-ttu-id="961f9-107">Description</span><span class="sxs-lookup"><span data-stu-id="961f9-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="961f9-108">`mdFieldDef` Jeton qui peut être utilisé pour récupérer des informations de champ.</span><span class="sxs-lookup"><span data-stu-id="961f9-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="961f9-109">Offset, en octets, des données de champ dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="961f9-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="961f9-110">Valeur [COR_TYPEID](cor-typeid-structure.md) qui identifie le type de ce champ.</span><span class="sxs-lookup"><span data-stu-id="961f9-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="961f9-111">Valeur d’énumération CorElementType qui indique le type du champ.</span><span class="sxs-lookup"><span data-stu-id="961f9-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="961f9-112">Notes</span><span class="sxs-lookup"><span data-stu-id="961f9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="961f9-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="961f9-113">Requirements</span></span>  
 <span data-ttu-id="961f9-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="961f9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="961f9-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="961f9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="961f9-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="961f9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="961f9-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="961f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961f9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="961f9-118">See also</span></span>

- [<span data-ttu-id="961f9-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="961f9-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="961f9-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="961f9-120">Debugging</span></span>](index.md)
