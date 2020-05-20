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
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616175"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="d19fd-102">ESymbolReadingPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="d19fd-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="d19fd-103">Contient des valeurs qui définissent la stratégie de lecture des fichiers de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="d19fd-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d19fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d19fd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="d19fd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d19fd-105">Members</span></span>  
  
|<span data-ttu-id="d19fd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d19fd-106">Member</span></span>|<span data-ttu-id="d19fd-107">Description</span><span class="sxs-lookup"><span data-stu-id="d19fd-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="d19fd-108">Spécifie que le débogueur doit toujours lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="d19fd-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="d19fd-109">Spécifie que le débogueur doit lire uniquement les fichiers PDB associés à des assemblys de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="d19fd-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="d19fd-110">Spécifie que le débogueur ne doit jamais lire les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="d19fd-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d19fd-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d19fd-111">Remarks</span></span>  
 <span data-ttu-id="d19fd-112">L' `ESymbolReadingPolicy` énumération est utilisée avec la méthode [ICLRDebugManager :: SetSymbolReadingPolicy (](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d19fd-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d19fd-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d19fd-113">Requirements</span></span>  
 <span data-ttu-id="d19fd-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d19fd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d19fd-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d19fd-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d19fd-116">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d19fd-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d19fd-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d19fd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19fd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d19fd-118">See also</span></span>

- [<span data-ttu-id="d19fd-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="d19fd-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
