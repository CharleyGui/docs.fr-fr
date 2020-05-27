---
title: CorErrorIfEmitOutOfOrder, énumération
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007429"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="a7424-102">CorErrorIfEmitOutOfOrder, énumération</span><span class="sxs-lookup"><span data-stu-id="a7424-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="a7424-103">Contient des valeurs d'indicateur qui précisent les conditions dans lesquelles un message d'erreur doit être généré quand les métadonnées sont émises de manière désordonnée.</span><span class="sxs-lookup"><span data-stu-id="a7424-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7424-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7424-104">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="a7424-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a7424-105">Members</span></span>  
  
|<span data-ttu-id="a7424-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a7424-106">Member</span></span>|<span data-ttu-id="a7424-107">Description</span><span class="sxs-lookup"><span data-stu-id="a7424-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="a7424-108">Indique le comportement par défaut, qui ne génère pas de messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a7424-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="a7424-109">Indique que le compilateur ne doit pas générer de messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a7424-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="a7424-110">Indique que le compilateur doit générer un message d’erreur lorsqu’un champ, une propriété, un événement, une méthode ou un paramètre est émis dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="a7424-111">Indique que le compilateur doit générer un message d’erreur lorsqu’une méthode est émise dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="a7424-112">Indique que le compilateur doit générer un message d’erreur lorsqu’un champ est émis dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="a7424-113">Indique que le compilateur doit générer un message d’erreur lorsqu’un paramètre est émis dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="a7424-114">Indique que le compilateur doit générer un message d’erreur lorsqu’une propriété est émise dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="a7424-115">Indique que le compilateur doit générer un message d’erreur lorsqu’un événement est émis dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="a7424-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7424-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a7424-116">Requirements</span></span>  
 <span data-ttu-id="a7424-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7424-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7424-118">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a7424-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a7424-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7424-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7424-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7424-120">See also</span></span>

- [<span data-ttu-id="a7424-121">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a7424-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
