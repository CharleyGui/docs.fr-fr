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
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124928"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="c8c53-102">ECustomDumpFlavor, énumération</span><span class="sxs-lookup"><span data-stu-id="c8c53-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="c8c53-103">Contient des valeurs qui indiquent les éléments à inclure dans un sous-ensemble personnalisé d’un dump de tas lors du signalement d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="c8c53-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8c53-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="c8c53-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c8c53-105">Members</span></span>  
  
|<span data-ttu-id="c8c53-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c8c53-106">Member</span></span>|<span data-ttu-id="c8c53-107">Description</span><span class="sxs-lookup"><span data-stu-id="c8c53-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="c8c53-108">Spécifie que le dump du tas personnalisé doit démarrer en tant que Minidump et inclure des données supplémentaires spécifiées par des instances [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) passées à la même méthode.</span><span class="sxs-lookup"><span data-stu-id="c8c53-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="c8c53-109">Spécifie que le dump du tas personnalisé doit collecter toutes les données d’état d’exécution qui n’ont pas été allouées dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="c8c53-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8c53-110">Notes</span><span class="sxs-lookup"><span data-stu-id="c8c53-110">Remarks</span></span>  
 <span data-ttu-id="c8c53-111">Un paramètre de type `ECustomDumpFlavor` est passé à la méthode [ICLRErrorReportingManager :: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c8c53-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8c53-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="c8c53-112">Requirements</span></span>  
 <span data-ttu-id="c8c53-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8c53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c53-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8c53-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8c53-115">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8c53-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8c53-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c53-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8c53-117">See also</span></span>

- [<span data-ttu-id="c8c53-118">ECustomDumpItemKind, énumération</span><span class="sxs-lookup"><span data-stu-id="c8c53-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="c8c53-119">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="c8c53-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="c8c53-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c8c53-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
