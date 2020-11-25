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
ms.openlocfilehash: bbdc68721378e6bbb09f5e4eade08e2e6e03b097
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729908"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="ae75b-102">StackOverflowType, énumération</span><span class="sxs-lookup"><span data-stu-id="ae75b-102">StackOverflowType Enumeration</span></span>

<span data-ttu-id="ae75b-103">Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="ae75b-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae75b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae75b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="ae75b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ae75b-105">Members</span></span>  
  
|<span data-ttu-id="ae75b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ae75b-106">Member</span></span>|<span data-ttu-id="ae75b-107">Description</span><span class="sxs-lookup"><span data-stu-id="ae75b-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="ae75b-108">Le dépassement de capacité de la pile a été provoqué par le moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ae75b-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="ae75b-109">Le dépassement de capacité de la pile a été provoqué par du code managé.</span><span class="sxs-lookup"><span data-stu-id="ae75b-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="ae75b-110">Le dépassement de capacité de la pile a été provoqué par du code non managé.</span><span class="sxs-lookup"><span data-stu-id="ae75b-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae75b-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae75b-111">Remarks</span></span>  

 <span data-ttu-id="ae75b-112">Ces informations sont passées à l’hôte via un appel à la méthode [IActionOnCLREvent :: OnEvent](iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ae75b-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae75b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae75b-113">Requirements</span></span>  

 <span data-ttu-id="ae75b-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae75b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae75b-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ae75b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae75b-116">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae75b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae75b-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae75b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae75b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae75b-118">See also</span></span>

- [<span data-ttu-id="ae75b-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="ae75b-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
