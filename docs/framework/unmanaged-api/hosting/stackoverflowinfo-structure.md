---
title: StackOverflowInfo, structure
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729926"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="cf183-102">StackOverflowInfo, structure</span><span class="sxs-lookup"><span data-stu-id="cf183-102">StackOverflowInfo Structure</span></span>

<span data-ttu-id="cf183-103">Stocke le type de dépassement qui s’est produit et les informations sur l’exception levée en raison du dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="cf183-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf183-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf183-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="cf183-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cf183-105">Members</span></span>  
  
|<span data-ttu-id="cf183-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cf183-106">Member</span></span>|<span data-ttu-id="cf183-107">Description</span><span class="sxs-lookup"><span data-stu-id="cf183-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="cf183-108">Valeur de l’énumération [StackOverflowType,](stackoverflowtype-enumeration.md) qui spécifie le type de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="cf183-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="cf183-109">Pointeur vers un objet Win32 `EXCEPTION_POINTERS` , qui contient un enregistrement d’exception avec une description indépendante de l’ordinateur d’une exception et un enregistrement de contexte avec une description dépendante de l’ordinateur du contexte du processeur au moment de l’exception.</span><span class="sxs-lookup"><span data-stu-id="cf183-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf183-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf183-110">Remarks</span></span>  

 <span data-ttu-id="cf183-111">Un `StackOverflowInfo` objet est passé à la méthode [IActionOnCLREvent :: OnEvent](iactiononclrevent-onevent-method.md) pour les `Event_StackOverflow` événements.</span><span class="sxs-lookup"><span data-stu-id="cf183-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf183-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf183-112">Requirements</span></span>  

 <span data-ttu-id="cf183-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf183-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf183-114">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="cf183-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="cf183-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf183-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf183-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf183-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf183-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf183-117">See also</span></span>

- [<span data-ttu-id="cf183-118">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="cf183-118">Hosting Structures</span></span>](hosting-structures.md)
