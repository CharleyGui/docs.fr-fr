---
title: StackOverflowType, énumération
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751134"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="2cc66-102">StackOverflowType, énumération</span><span class="sxs-lookup"><span data-stu-id="2cc66-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="2cc66-103">Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="2cc66-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc66-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="2cc66-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2cc66-105">Members</span></span>  
  
|<span data-ttu-id="2cc66-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2cc66-106">Member</span></span>|<span data-ttu-id="2cc66-107">Description</span><span class="sxs-lookup"><span data-stu-id="2cc66-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="2cc66-108">Le dépassement de capacité de pile a été provoqué par le moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2cc66-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="2cc66-109">Le dépassement de capacité de pile a été provoqué par le code managé.</span><span class="sxs-lookup"><span data-stu-id="2cc66-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="2cc66-110">Le dépassement de capacité de pile a été provoqué par le code non managé.</span><span class="sxs-lookup"><span data-stu-id="2cc66-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cc66-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2cc66-111">Remarks</span></span>  
 <span data-ttu-id="2cc66-112">Ces informations sont passées à l’hôte via un appel à la [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="2cc66-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cc66-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cc66-113">Requirements</span></span>  
 <span data-ttu-id="2cc66-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cc66-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc66-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cc66-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cc66-116">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cc66-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cc66-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc66-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc66-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cc66-118">See also</span></span>

- [<span data-ttu-id="2cc66-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2cc66-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
