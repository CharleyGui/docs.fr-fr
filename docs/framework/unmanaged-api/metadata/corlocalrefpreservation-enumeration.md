---
title: CorLocalRefPreservation, énumération
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6338034d6714e8770e06ff61994fdf4433eb1684
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781789"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="15b89-102">CorLocalRefPreservation, énumération</span><span class="sxs-lookup"><span data-stu-id="15b89-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="15b89-103">Contient des valeurs d'indicateur pour le traitement des références locales.</span><span class="sxs-lookup"><span data-stu-id="15b89-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15b89-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="15b89-105">Membres</span><span class="sxs-lookup"><span data-stu-id="15b89-105">Members</span></span>  
  
|<span data-ttu-id="15b89-106">Membre</span><span class="sxs-lookup"><span data-stu-id="15b89-106">Member</span></span>|<span data-ttu-id="15b89-107">Description</span><span class="sxs-lookup"><span data-stu-id="15b89-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="15b89-108">Ne conserver aucune référence locale.</span><span class="sxs-lookup"><span data-stu-id="15b89-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="15b89-109">Conserve les références de type local.</span><span class="sxs-lookup"><span data-stu-id="15b89-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="15b89-110">Conserve les références de membre locale.</span><span class="sxs-lookup"><span data-stu-id="15b89-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15b89-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15b89-111">Requirements</span></span>  
 <span data-ttu-id="15b89-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b89-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b89-113">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="15b89-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="15b89-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15b89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b89-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15b89-115">See also</span></span>

- [<span data-ttu-id="15b89-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="15b89-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
