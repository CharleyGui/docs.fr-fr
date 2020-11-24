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
ms.openlocfilehash: 49b0298f4fa776c93f89ac380ce65568b493379b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677113"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="ec7bc-102">CorLocalRefPreservation, énumération</span><span class="sxs-lookup"><span data-stu-id="ec7bc-102">CorLocalRefPreservation Enumeration</span></span>

<span data-ttu-id="ec7bc-103">Contient des valeurs d'indicateur pour le traitement des références locales.</span><span class="sxs-lookup"><span data-stu-id="ec7bc-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec7bc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="ec7bc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ec7bc-105">Members</span></span>  
  
|<span data-ttu-id="ec7bc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ec7bc-106">Member</span></span>|<span data-ttu-id="ec7bc-107">Description</span><span class="sxs-lookup"><span data-stu-id="ec7bc-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="ec7bc-108">Ne conserver aucune référence locale.</span><span class="sxs-lookup"><span data-stu-id="ec7bc-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="ec7bc-109">Conserver les références de type local.</span><span class="sxs-lookup"><span data-stu-id="ec7bc-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="ec7bc-110">Conserver les références des membres locaux.</span><span class="sxs-lookup"><span data-stu-id="ec7bc-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec7bc-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec7bc-111">Requirements</span></span>  

 <span data-ttu-id="ec7bc-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec7bc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec7bc-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ec7bc-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ec7bc-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec7bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7bc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec7bc-115">See also</span></span>

- [<span data-ttu-id="ec7bc-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ec7bc-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
