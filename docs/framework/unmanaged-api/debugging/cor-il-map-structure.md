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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74f515626f5001cbea1a25e8268338c588524bde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740537"
---
# <a name="corilmap-structure"></a><span data-ttu-id="fea3f-102">COR_IL_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="fea3f-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="fea3f-103">Spécifie des modifications dans le décalage relatif d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="fea3f-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fea3f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="fea3f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fea3f-105">Members</span></span>  
  
|<span data-ttu-id="fea3f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fea3f-106">Member</span></span>|<span data-ttu-id="fea3f-107">Description</span><span class="sxs-lookup"><span data-stu-id="fea3f-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="fea3f-108">L’ancien intermediate langage MSIL (Microsoft) décalage par rapport au début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fea3f-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="fea3f-109">Le nouveau décalage MSIL par rapport au début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fea3f-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="fea3f-110">`true` Si le mappage est connu pour être précis ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="fea3f-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea3f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="fea3f-111">Remarks</span></span>  
 <span data-ttu-id="fea3f-112">Le format de la carte est comme suit : Le débogueur suppose que `oldOffset` fait référence à un offset MSIL dans le code MSIL non modifié d’origine.</span><span class="sxs-lookup"><span data-stu-id="fea3f-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="fea3f-113">Le `newOffset` paramètre fait référence à l’offset MSIL correspondant dans le nouveau code instrumenté.</span><span class="sxs-lookup"><span data-stu-id="fea3f-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="fea3f-114">Pour l’exécution pas à pas pour fonctionner correctement, les conditions suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="fea3f-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="fea3f-115">Le mappage doit être trié dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="fea3f-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="fea3f-116">Code MSIL instrumenté ne doit pas être réorganisé.</span><span class="sxs-lookup"><span data-stu-id="fea3f-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="fea3f-117">Code MSIL d’origine ne doit pas être supprimé.</span><span class="sxs-lookup"><span data-stu-id="fea3f-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="fea3f-118">Le mappage doit inclure des entrées pour tous les points de séquence fichier de programme (PDB) de la base de données de la carte.</span><span class="sxs-lookup"><span data-stu-id="fea3f-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="fea3f-119">Le mappage n’interpole pas les entrées manquantes.</span><span class="sxs-lookup"><span data-stu-id="fea3f-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="fea3f-120">L’exemple suivant montre un mappage et ses résultats.</span><span class="sxs-lookup"><span data-stu-id="fea3f-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="fea3f-121">Carte :</span><span class="sxs-lookup"><span data-stu-id="fea3f-121">Map:</span></span>  
  
- <span data-ttu-id="fea3f-122">ancien offset 0, 0 nouveau décalage</span><span class="sxs-lookup"><span data-stu-id="fea3f-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="fea3f-123">ancien offset 5, 10 nouveau décalage</span><span class="sxs-lookup"><span data-stu-id="fea3f-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="fea3f-124">ancien offset 9, 20 nouveau décalage</span><span class="sxs-lookup"><span data-stu-id="fea3f-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="fea3f-125">Résultats :</span><span class="sxs-lookup"><span data-stu-id="fea3f-125">Results:</span></span>  
  
- <span data-ttu-id="fea3f-126">Un ancien offset de 0, 1, 2, 3 ou 4 sera mappé à un nouveau décalage de 0.</span><span class="sxs-lookup"><span data-stu-id="fea3f-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="fea3f-127">Un ancien offset de 5, 6, 7 ou 8 sera mappé à nouveau décalage de 10.</span><span class="sxs-lookup"><span data-stu-id="fea3f-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="fea3f-128">Un ancien offset de 9 ou version ultérieure sera mappé à nouveau décalage de 20.</span><span class="sxs-lookup"><span data-stu-id="fea3f-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="fea3f-129">Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien offset 0.</span><span class="sxs-lookup"><span data-stu-id="fea3f-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="fea3f-130">Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien offset 5.</span><span class="sxs-lookup"><span data-stu-id="fea3f-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="fea3f-131">Un nouveau décalage supérieur ou égal à 20 sera mappé à l’ancien offset 9.</span><span class="sxs-lookup"><span data-stu-id="fea3f-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea3f-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fea3f-132">Requirements</span></span>  
 <span data-ttu-id="fea3f-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea3f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea3f-134">**En-tête :** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fea3f-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="fea3f-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fea3f-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fea3f-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea3f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea3f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fea3f-137">See also</span></span>

- [<span data-ttu-id="fea3f-138">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="fea3f-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="fea3f-139">Débogage</span><span class="sxs-lookup"><span data-stu-id="fea3f-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
