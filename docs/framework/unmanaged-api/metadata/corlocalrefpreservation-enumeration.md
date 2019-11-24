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
ms.openlocfilehash: 706ea37101f9f961e92d8cef2cf508c1dd0d56c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450244"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="ea5ec-102">CorLocalRefPreservation, énumération</span><span class="sxs-lookup"><span data-stu-id="ea5ec-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="ea5ec-103">Contient des valeurs d'indicateur pour le traitement des références locales.</span><span class="sxs-lookup"><span data-stu-id="ea5ec-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea5ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea5ec-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="ea5ec-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ea5ec-105">Members</span></span>  
  
|<span data-ttu-id="ea5ec-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ea5ec-106">Member</span></span>|<span data-ttu-id="ea5ec-107">Description</span><span class="sxs-lookup"><span data-stu-id="ea5ec-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="ea5ec-108">Preserve no local references.</span><span class="sxs-lookup"><span data-stu-id="ea5ec-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="ea5ec-109">Preserve local type references.</span><span class="sxs-lookup"><span data-stu-id="ea5ec-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="ea5ec-110">Preserve local member references.</span><span class="sxs-lookup"><span data-stu-id="ea5ec-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea5ec-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea5ec-111">Requirements</span></span>  
 <span data-ttu-id="ea5ec-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea5ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea5ec-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ea5ec-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ea5ec-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea5ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5ec-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea5ec-115">See also</span></span>

- [<span data-ttu-id="ea5ec-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ea5ec-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
