---
title: ESymbolReadingPolicy, énumération
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138204"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="6cdfa-102">ESymbolReadingPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="6cdfa-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="6cdfa-103">Contient des valeurs qui définissent la stratégie de lecture des fichiers de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="6cdfa-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cdfa-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="6cdfa-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6cdfa-105">Members</span></span>  
  
|<span data-ttu-id="6cdfa-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6cdfa-106">Member</span></span>|<span data-ttu-id="6cdfa-107">Description</span><span class="sxs-lookup"><span data-stu-id="6cdfa-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="6cdfa-108">Spécifie que le débogueur doit toujours lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="6cdfa-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="6cdfa-109">Spécifie que le débogueur doit lire uniquement les fichiers PDB associés à des assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="6cdfa-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="6cdfa-110">Spécifie que le débogueur ne doit jamais lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="6cdfa-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cdfa-111">Notes</span><span class="sxs-lookup"><span data-stu-id="6cdfa-111">Remarks</span></span>  
 <span data-ttu-id="6cdfa-112">L’énumération `ESymbolReadingPolicy` est utilisée avec la méthode [ICLRDebugManager :: SetSymbolReadingPolicy (](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6cdfa-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdfa-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="6cdfa-113">Requirements</span></span>  
 <span data-ttu-id="6cdfa-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cdfa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cdfa-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6cdfa-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cdfa-116">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6cdfa-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cdfa-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cdfa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdfa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cdfa-118">See also</span></span>

- [<span data-ttu-id="6cdfa-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="6cdfa-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
