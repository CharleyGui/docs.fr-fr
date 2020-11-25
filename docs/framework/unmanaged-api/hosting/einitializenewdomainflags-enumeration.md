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
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724323"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="acfdb-102">EInitializeNewDomainFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="acfdb-102">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="acfdb-103">Permet à l’hôte de fournir au runtime des informations sur l’initialisation d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="acfdb-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acfdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acfdb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="acfdb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="acfdb-105">Members</span></span>  
  
|<span data-ttu-id="acfdb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="acfdb-106">Member</span></span>|<span data-ttu-id="acfdb-107">Description</span><span class="sxs-lookup"><span data-stu-id="acfdb-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="acfdb-108">Aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="acfdb-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="acfdb-109">Informe le common language runtime (CLR) que l’hôte n’apporte pas de modifications à l’état de sécurité du domaine d’application dans la <xref:System.AppDomainManager.InitializeNewDomain%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="acfdb-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acfdb-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="acfdb-110">Remarks</span></span>  

 <span data-ttu-id="acfdb-111">La méthode [ICLRDomainManager :: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) prend un paramètre de type `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="acfdb-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acfdb-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="acfdb-112">Requirements</span></span>  

 <span data-ttu-id="acfdb-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acfdb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acfdb-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="acfdb-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="acfdb-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="acfdb-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acfdb-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acfdb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfdb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acfdb-117">See also</span></span>

- [<span data-ttu-id="acfdb-118">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="acfdb-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="acfdb-119">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="acfdb-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
