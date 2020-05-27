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
ms.openlocfilehash: 42cb4e76bb77aebcee3b28035635a877513cdc04
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008987"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="caf8e-102">CorLocalRefPreservation, énumération</span><span class="sxs-lookup"><span data-stu-id="caf8e-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="caf8e-103">Contient des valeurs d'indicateur pour le traitement des références locales.</span><span class="sxs-lookup"><span data-stu-id="caf8e-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caf8e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="caf8e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="caf8e-105">Members</span></span>  
  
|<span data-ttu-id="caf8e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="caf8e-106">Member</span></span>|<span data-ttu-id="caf8e-107">Description</span><span class="sxs-lookup"><span data-stu-id="caf8e-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="caf8e-108">Ne conserver aucune référence locale.</span><span class="sxs-lookup"><span data-stu-id="caf8e-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="caf8e-109">Conserver les références de type local.</span><span class="sxs-lookup"><span data-stu-id="caf8e-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="caf8e-110">Conserver les références des membres locaux.</span><span class="sxs-lookup"><span data-stu-id="caf8e-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caf8e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="caf8e-111">Requirements</span></span>  
 <span data-ttu-id="caf8e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caf8e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf8e-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="caf8e-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="caf8e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf8e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caf8e-115">See also</span></span>

- [<span data-ttu-id="caf8e-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="caf8e-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
