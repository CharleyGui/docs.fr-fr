---
title: COR_IL_MAP, structure
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132344"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="38f87-102">COR_IL_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="38f87-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="38f87-103">Spécifie des modifications dans le décalage relatif d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="38f87-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38f87-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="38f87-105">Membres</span><span class="sxs-lookup"><span data-stu-id="38f87-105">Members</span></span>  
  
|<span data-ttu-id="38f87-106">Membre</span><span class="sxs-lookup"><span data-stu-id="38f87-106">Member</span></span>|<span data-ttu-id="38f87-107">Description</span><span class="sxs-lookup"><span data-stu-id="38f87-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="38f87-108">Ancien offset MSIL (Microsoft Intermediate Language) par rapport au début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="38f87-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="38f87-109">Nouveau décalage MSIL par rapport au début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="38f87-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="38f87-110">`true` si le mappage est reconnu comme étant exact ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="38f87-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38f87-111">Notes</span><span class="sxs-lookup"><span data-stu-id="38f87-111">Remarks</span></span>  
 <span data-ttu-id="38f87-112">Le format du mappage est le suivant : le débogueur suppose que `oldOffset` fait référence à un décalage MSIL dans le code MSIL non modifié d’origine.</span><span class="sxs-lookup"><span data-stu-id="38f87-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="38f87-113">Le paramètre `newOffset` fait référence à l’offset MSIL correspondant dans le nouveau code instrumenté.</span><span class="sxs-lookup"><span data-stu-id="38f87-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="38f87-114">Pour que l’exécution pas à pas fonctionne correctement, les conditions suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="38f87-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="38f87-115">La carte doit être triée par ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="38f87-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="38f87-116">Le code MSIL instrumenté ne doit pas être réorganisé.</span><span class="sxs-lookup"><span data-stu-id="38f87-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="38f87-117">Le code MSIL d’origine ne doit pas être supprimé.</span><span class="sxs-lookup"><span data-stu-id="38f87-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="38f87-118">Le mappage doit inclure des entrées pour mapper tous les points de séquence à partir du fichier de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="38f87-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="38f87-119">Le mappage n’interpole pas les entrées manquantes.</span><span class="sxs-lookup"><span data-stu-id="38f87-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="38f87-120">L’exemple suivant montre un mappage et ses résultats.</span><span class="sxs-lookup"><span data-stu-id="38f87-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="38f87-121">Canal</span><span class="sxs-lookup"><span data-stu-id="38f87-121">Map:</span></span>  
  
- <span data-ttu-id="38f87-122">0 ancien décalage, 0 nouveau décalage</span><span class="sxs-lookup"><span data-stu-id="38f87-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="38f87-123">5 ancien décalage, 10 nouveaux décalages</span><span class="sxs-lookup"><span data-stu-id="38f87-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="38f87-124">9 ancien décalage, 20 nouveau décalage</span><span class="sxs-lookup"><span data-stu-id="38f87-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="38f87-125">About</span><span class="sxs-lookup"><span data-stu-id="38f87-125">Results:</span></span>  
  
- <span data-ttu-id="38f87-126">Un ancien décalage de 0, 1, 2, 3 ou 4 sera mappé à un nouveau décalage de 0.</span><span class="sxs-lookup"><span data-stu-id="38f87-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="38f87-127">Un ancien décalage de 5, 6, 7 ou 8 sera mappé au nouveau décalage 10.</span><span class="sxs-lookup"><span data-stu-id="38f87-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="38f87-128">Un ancien décalage de 9 ou plus sera mappé au nouveau décalage 20.</span><span class="sxs-lookup"><span data-stu-id="38f87-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="38f87-129">Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien décalage 0.</span><span class="sxs-lookup"><span data-stu-id="38f87-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="38f87-130">Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien décalage 5.</span><span class="sxs-lookup"><span data-stu-id="38f87-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="38f87-131">Un nouveau décalage de 20 ou plus sera mappé à l’ancien décalage 9.</span><span class="sxs-lookup"><span data-stu-id="38f87-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f87-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="38f87-132">Requirements</span></span>  
 <span data-ttu-id="38f87-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f87-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f87-134">**En-tête :** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="38f87-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="38f87-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38f87-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f87-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f87-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f87-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38f87-137">See also</span></span>

- [<span data-ttu-id="38f87-138">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="38f87-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="38f87-139">Débogage</span><span class="sxs-lookup"><span data-stu-id="38f87-139">Debugging</span></span>](index.md)
