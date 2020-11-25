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
ms.openlocfilehash: ae8e907d0e0d6ef5030b3e9aa1f1b3dcef50193e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726624"
---
# <a name="cor_field-structure"></a><span data-ttu-id="aebd3-102">COR_FIELD, structure</span><span class="sxs-lookup"><span data-stu-id="aebd3-102">COR_FIELD Structure</span></span>

<span data-ttu-id="aebd3-103">Fournit des informations sur un champ dans un objet.</span><span class="sxs-lookup"><span data-stu-id="aebd3-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aebd3-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="aebd3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="aebd3-105">Members</span></span>  
  
|<span data-ttu-id="aebd3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="aebd3-106">Member</span></span>|<span data-ttu-id="aebd3-107">Description</span><span class="sxs-lookup"><span data-stu-id="aebd3-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="aebd3-108">`mdFieldDef`Jeton qui peut être utilisé pour récupérer des informations de champ.</span><span class="sxs-lookup"><span data-stu-id="aebd3-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="aebd3-109">Offset, en octets, des données de champ dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="aebd3-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="aebd3-110">Valeur [COR_TYPEID](cor-typeid-structure.md) qui identifie le type de ce champ.</span><span class="sxs-lookup"><span data-stu-id="aebd3-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="aebd3-111">Valeur d’énumération CorElementType qui indique le type du champ.</span><span class="sxs-lookup"><span data-stu-id="aebd3-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aebd3-112">Notes</span><span class="sxs-lookup"><span data-stu-id="aebd3-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aebd3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aebd3-113">Requirements</span></span>  

 <span data-ttu-id="aebd3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aebd3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aebd3-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aebd3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aebd3-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aebd3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aebd3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aebd3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebd3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aebd3-118">See also</span></span>

- [<span data-ttu-id="aebd3-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="aebd3-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="aebd3-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="aebd3-120">Debugging</span></span>](index.md)
