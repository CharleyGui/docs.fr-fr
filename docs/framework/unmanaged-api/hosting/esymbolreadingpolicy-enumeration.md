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
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733709"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="349b3-102">ESymbolReadingPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="349b3-102">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="349b3-103">Contient des valeurs qui définissent la stratégie de lecture des fichiers de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="349b3-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="349b3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="349b3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="349b3-105">Members</span></span>  
  
|<span data-ttu-id="349b3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="349b3-106">Member</span></span>|<span data-ttu-id="349b3-107">Description</span><span class="sxs-lookup"><span data-stu-id="349b3-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="349b3-108">Spécifie que le débogueur doit toujours lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="349b3-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="349b3-109">Spécifie que le débogueur doit lire uniquement les fichiers PDB associés à des assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="349b3-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="349b3-110">Spécifie que le débogueur ne doit jamais lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="349b3-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="349b3-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="349b3-111">Remarks</span></span>  

 <span data-ttu-id="349b3-112">L' `ESymbolReadingPolicy` énumération est utilisée avec la méthode [ICLRDebugManager :: SetSymbolReadingPolicy (](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="349b3-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="349b3-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="349b3-113">Requirements</span></span>  

 <span data-ttu-id="349b3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="349b3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="349b3-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="349b3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="349b3-116">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="349b3-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="349b3-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="349b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349b3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="349b3-118">See also</span></span>

- [<span data-ttu-id="349b3-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="349b3-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
