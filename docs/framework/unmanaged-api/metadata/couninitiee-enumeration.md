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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d8189365a73e85c0b9f5efb2aa03074385a3fb8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750746"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="85aa7-102">COUNINITIEE, énumération</span><span class="sxs-lookup"><span data-stu-id="85aa7-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="85aa7-103">Spécifie les constantes utilisées par [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) lors de l’initialisation du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="85aa7-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85aa7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85aa7-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="85aa7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="85aa7-105">Members</span></span>  
  
|<span data-ttu-id="85aa7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="85aa7-106">Member</span></span>|<span data-ttu-id="85aa7-107">Description</span><span class="sxs-lookup"><span data-stu-id="85aa7-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="85aa7-108">Indique le mode de désinitialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="85aa7-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="85aa7-109">Indique le mode de désinitialisation pour décharger un assembly.</span><span class="sxs-lookup"><span data-stu-id="85aa7-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85aa7-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="85aa7-110">Requirements</span></span>  
 <span data-ttu-id="85aa7-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85aa7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85aa7-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85aa7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85aa7-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85aa7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85aa7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85aa7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85aa7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85aa7-115">See also</span></span>

- [<span data-ttu-id="85aa7-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="85aa7-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
