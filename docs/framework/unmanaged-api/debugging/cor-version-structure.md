---
title: COR_VERSION, structure
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: 874c0520482cc5a3bbfcdd17924edee84fe91ff5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675319"
---
# <a name="cor_version-structure"></a><span data-ttu-id="781c8-102">COR_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="781c8-102">COR_VERSION Structure</span></span>

<span data-ttu-id="781c8-103">Stocke le numéro de version en quatre parties du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="781c8-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="781c8-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="781c8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="781c8-105">Members</span></span>  
  
|<span data-ttu-id="781c8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="781c8-106">Member</span></span>|<span data-ttu-id="781c8-107">Description</span><span class="sxs-lookup"><span data-stu-id="781c8-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="781c8-108">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="781c8-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="781c8-109">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="781c8-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="781c8-110">Numéro de build.</span><span class="sxs-lookup"><span data-stu-id="781c8-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="781c8-111">Numéro de sous-Build.</span><span class="sxs-lookup"><span data-stu-id="781c8-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="781c8-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="781c8-112">Remarks</span></span>  

 <span data-ttu-id="781c8-113">Si le numéro de version est 1.0.3705.288, 1 est le numéro de version principale, 0 est le numéro de version mineure, 3705 est le numéro de build et 288 est le numéro de sous-Build.</span><span class="sxs-lookup"><span data-stu-id="781c8-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781c8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="781c8-114">Requirements</span></span>  

 <span data-ttu-id="781c8-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781c8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781c8-116">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="781c8-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="781c8-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="781c8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="781c8-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781c8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="781c8-119">See also</span></span>

- [<span data-ttu-id="781c8-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="781c8-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="781c8-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="781c8-121">Debugging</span></span>](index.md)
