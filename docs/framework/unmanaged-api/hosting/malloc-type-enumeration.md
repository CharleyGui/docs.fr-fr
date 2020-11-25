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
ms.openlocfilehash: fe58a519d0feac0da49e7778247da1ef538f8b83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730030"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="f6d61-102">MALLOC_TYPE (énumération)</span><span class="sxs-lookup"><span data-stu-id="f6d61-102">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="f6d61-103">Contient des valeurs qui spécifient les caractéristiques de la mémoire qui est allouée.</span><span class="sxs-lookup"><span data-stu-id="f6d61-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6d61-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="f6d61-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f6d61-105">Members</span></span>  
  
|<span data-ttu-id="f6d61-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f6d61-106">Member</span></span>|<span data-ttu-id="f6d61-107">Description</span><span class="sxs-lookup"><span data-stu-id="f6d61-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="f6d61-108">La mémoire allouée peut contenir un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="f6d61-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="f6d61-109">La mémoire allouée est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f6d61-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="f6d61-110">Autrement dit, la mémoire est accessible par plusieurs threads sans aucune synchronisation.</span><span class="sxs-lookup"><span data-stu-id="f6d61-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="f6d61-111">Si cet indicateur n’est pas défini, les appels sur l’objet doivent être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="f6d61-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6d61-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6d61-112">Requirements</span></span>  

 <span data-ttu-id="f6d61-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d61-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d61-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f6d61-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6d61-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6d61-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6d61-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d61-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d61-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6d61-117">See also</span></span>

- [<span data-ttu-id="f6d61-118">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f6d61-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
