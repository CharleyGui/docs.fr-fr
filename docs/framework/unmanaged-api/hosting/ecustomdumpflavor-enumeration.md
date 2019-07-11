---
title: ECustomDumpFlavor, énumération
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a416a51f5121f29d373fcfdfa6b0597d9b10ded5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779383"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="58e2d-102">ECustomDumpFlavor, énumération</span><span class="sxs-lookup"><span data-stu-id="58e2d-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="58e2d-103">Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un segment de mémoire de vidage lors du signalement des erreurs.</span><span class="sxs-lookup"><span data-stu-id="58e2d-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e2d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="58e2d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="58e2d-105">Members</span></span>  
  
|<span data-ttu-id="58e2d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="58e2d-106">Member</span></span>|<span data-ttu-id="58e2d-107">Description</span><span class="sxs-lookup"><span data-stu-id="58e2d-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="58e2d-108">Spécifie que le dump du tas personnalisé doit démarrer en tant qu’un minidump et inclure les données supplémentaires spécifiées par les [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passées à la même méthode.</span><span class="sxs-lookup"><span data-stu-id="58e2d-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="58e2d-109">Spécifie que le dump du tas personnalisé doit rassembler toutes les données d’état d’exécution qui ne sont pas allouées dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="58e2d-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e2d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="58e2d-110">Remarks</span></span>  
 <span data-ttu-id="58e2d-111">Un paramètre de type `ECustomDumpFlavor` est passé à la [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="58e2d-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e2d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58e2d-112">Requirements</span></span>  
 <span data-ttu-id="58e2d-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58e2d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e2d-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58e2d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58e2d-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58e2d-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58e2d-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e2d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e2d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58e2d-117">See also</span></span>

- [<span data-ttu-id="58e2d-118">ECustomDumpItemKind, énumération</span><span class="sxs-lookup"><span data-stu-id="58e2d-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="58e2d-119">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="58e2d-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="58e2d-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="58e2d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
