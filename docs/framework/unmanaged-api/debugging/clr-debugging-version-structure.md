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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132416"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="2fd69-102">CLR_DEBUGGING_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="2fd69-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="2fd69-103">Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="2fd69-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fd69-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2fd69-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2fd69-105">Members</span></span>  
  
|<span data-ttu-id="2fd69-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2fd69-106">Member</span></span>|<span data-ttu-id="2fd69-107">Description</span><span class="sxs-lookup"><span data-stu-id="2fd69-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="2fd69-108">Numéro de version de la structure</span><span class="sxs-lookup"><span data-stu-id="2fd69-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="2fd69-109">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="2fd69-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="2fd69-110">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="2fd69-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="2fd69-111">Numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="2fd69-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="2fd69-112">Numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="2fd69-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fd69-113">Notes</span><span class="sxs-lookup"><span data-stu-id="2fd69-113">Remarks</span></span>  
 <span data-ttu-id="2fd69-114">La structure `CLR_DEBUGGING_VERSION` est identique à la structure COR_VERSION. Toutefois, la structure `CLR_DEBUGGING_VERSION` fournit un champ de version de structure supplémentaire (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="2fd69-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="2fd69-115">Actuellement, ce champ doit avoir la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="2fd69-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd69-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="2fd69-116">Requirements</span></span>  
 <span data-ttu-id="2fd69-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd69-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd69-118">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="2fd69-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="2fd69-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd69-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd69-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd69-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd69-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fd69-121">See also</span></span>

- [<span data-ttu-id="2fd69-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="2fd69-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2fd69-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="2fd69-123">Debugging</span></span>](index.md)
