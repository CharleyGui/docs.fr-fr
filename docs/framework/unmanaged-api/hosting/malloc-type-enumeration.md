---
title: MALLOC_TYPE (énumération)
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090823"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="0c0c4-102">MALLOC_TYPE (énumération)</span><span class="sxs-lookup"><span data-stu-id="0c0c4-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="0c0c4-103">Contient des valeurs qui spécifient les caractéristiques de la mémoire qui est allouée.</span><span class="sxs-lookup"><span data-stu-id="0c0c4-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c0c4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0c0c4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0c0c4-105">Members</span></span>  
  
|<span data-ttu-id="0c0c4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0c0c4-106">Member</span></span>|<span data-ttu-id="0c0c4-107">Description</span><span class="sxs-lookup"><span data-stu-id="0c0c4-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="0c0c4-108">La mémoire allouée peut contenir un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="0c0c4-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="0c0c4-109">La mémoire allouée est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="0c0c4-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="0c0c4-110">Autrement dit, la mémoire est accessible par plusieurs threads sans aucune synchronisation.</span><span class="sxs-lookup"><span data-stu-id="0c0c4-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="0c0c4-111">Si cet indicateur n’est pas défini, les appels sur l’objet doivent être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="0c0c4-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c0c4-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="0c0c4-112">Requirements</span></span>  
 <span data-ttu-id="0c0c4-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c0c4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c0c4-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c0c4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c0c4-115">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c0c4-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c0c4-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c0c4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0c4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c0c4-117">See also</span></span>

- [<span data-ttu-id="0c0c4-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="0c0c4-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
