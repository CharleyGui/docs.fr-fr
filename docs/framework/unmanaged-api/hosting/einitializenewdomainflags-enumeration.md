---
title: EInitializeNewDomainFlags, énumération
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616227"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="b1bdc-102">EInitializeNewDomainFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="b1bdc-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="b1bdc-103">Permet à l’hôte de fournir au runtime des informations sur l’initialisation d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1bdc-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b1bdc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b1bdc-105">Members</span></span>  
  
|<span data-ttu-id="b1bdc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b1bdc-106">Member</span></span>|<span data-ttu-id="b1bdc-107">Description</span><span class="sxs-lookup"><span data-stu-id="b1bdc-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="b1bdc-108">Aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="b1bdc-109">Informe le common language runtime (CLR) que l’hôte n’apporte pas de modifications à l’état de sécurité du domaine d’application dans la <xref:System.AppDomainManager.InitializeNewDomain%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1bdc-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b1bdc-110">Remarks</span></span>  
 <span data-ttu-id="b1bdc-111">La méthode [ICLRDomainManager :: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) prend un paramètre de type `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="b1bdc-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bdc-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b1bdc-112">Requirements</span></span>  
 <span data-ttu-id="b1bdc-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bdc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bdc-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1bdc-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1bdc-115">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1bdc-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1bdc-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bdc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bdc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1bdc-117">See also</span></span>

- [<span data-ttu-id="b1bdc-118">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="b1bdc-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="b1bdc-119">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="b1bdc-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
