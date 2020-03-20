---
title: COUNINITIEE, énumération
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176121"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="e770b-102">COUNINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="e770b-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="e770b-103">Spécifie les constantes utilisées par [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) lors de l’initialisation du temps de course de langue commune.</span><span class="sxs-lookup"><span data-stu-id="e770b-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e770b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e770b-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="e770b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e770b-105">Members</span></span>  
  
|<span data-ttu-id="e770b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e770b-106">Member</span></span>|<span data-ttu-id="e770b-107">Description</span><span class="sxs-lookup"><span data-stu-id="e770b-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="e770b-108">Indique le mode d’uninitalisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="e770b-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="e770b-109">Indique le mode d’uninitalisation pour décharger un assemblage.</span><span class="sxs-lookup"><span data-stu-id="e770b-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e770b-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e770b-110">Requirements</span></span>  
 <span data-ttu-id="e770b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e770b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e770b-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="e770b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e770b-113">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e770b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e770b-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e770b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e770b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e770b-115">See also</span></span>

- [<span data-ttu-id="e770b-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e770b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
