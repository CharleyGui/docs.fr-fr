---
title: CLR_DEBUGGING_VERSION, structure
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274088"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="ae6dd-102">CLR_DEBUGGING_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="ae6dd-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="ae6dd-103">Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae6dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae6dd-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="ae6dd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ae6dd-105">Members</span></span>  
  
|<span data-ttu-id="ae6dd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ae6dd-106">Member</span></span>|<span data-ttu-id="ae6dd-107">Description</span><span class="sxs-lookup"><span data-stu-id="ae6dd-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="ae6dd-108">Numéro de version de la structure</span><span class="sxs-lookup"><span data-stu-id="ae6dd-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="ae6dd-109">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="ae6dd-110">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="ae6dd-111">Numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="ae6dd-112">Numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae6dd-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ae6dd-113">Remarks</span></span>  
 <span data-ttu-id="ae6dd-114">Toutefois, la structure est la même que la structure COR_VERSION, mais `CLR_DEBUGGING_VERSION` la structure fournit un champ de version de`wStructVersion`structure supplémentaire (). `CLR_DEBUGGING_VERSION`</span><span class="sxs-lookup"><span data-stu-id="ae6dd-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="ae6dd-115">Actuellement, ce champ doit avoir la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="ae6dd-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae6dd-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae6dd-116">Requirements</span></span>  
 <span data-ttu-id="ae6dd-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae6dd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae6dd-118">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ae6dd-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ae6dd-119">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae6dd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae6dd-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae6dd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6dd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae6dd-121">See also</span></span>

- [<span data-ttu-id="ae6dd-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ae6dd-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ae6dd-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="ae6dd-123">Debugging</span></span>](index.md)
