---
title: ICorDebugModule2::ApplyChanges, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212215"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="5d8ad-102">ICorDebugModule2::ApplyChanges, méthode</span><span class="sxs-lookup"><span data-stu-id="5d8ad-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="5d8ad-103">Applique les modifications apportées aux métadonnées et les modifications apportées au code MSIL (Microsoft Intermediate Language) au processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d8ad-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d8ad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d8ad-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="5d8ad-106">dans Taille, en octets, des métadonnées Delta.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="5d8ad-107">dans Mémoire tampon qui contient les métadonnées Delta.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="5d8ad-108">L’adresse de la mémoire tampon est retournée à partir de la méthode [IMetaDataEmit2 :: SaveDeltaToMemory,](../metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5d8ad-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="5d8ad-109">Les adresses virtuelles relatives (RVA) dans les métadonnées doivent être relatives au début du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="5d8ad-110">dans Taille, en octets, du code MSIL Delta.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="5d8ad-111">dans Mémoire tampon qui contient le code MSIL mis à jour.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d8ad-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d8ad-112">Remarks</span></span>  
 <span data-ttu-id="5d8ad-113">Le `pbMetadata` paramètre est dans un format de métadonnées Delta spécial (comme sortie par [IMetaDataEmit2 :: SaveDeltaToMemory,](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="5d8ad-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="5d8ad-114">`pbMetadata`prend les métadonnées précédentes comme base et décrit les modifications individuelles à appliquer à cette base.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="5d8ad-115">En revanche, le `pbIL[` paramètre] contient le nouveau MSIL pour la méthode mise à jour et est destiné à remplacer complètement le code MSIL précédent pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="5d8ad-116">Lorsque le MSIL Delta et les métadonnées ont été créés dans la mémoire du débogueur, le débogueur appelle `ApplyChanges` pour envoyer les modifications dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5d8ad-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="5d8ad-117">Le Runtime met à jour ses tables de métadonnées, place le nouveau MSIL dans le processus et configure une compilation juste-à-temps (JIT) du nouveau MSIL.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="5d8ad-118">Lorsque les modifications ont été appliquées, le débogueur doit appeler [IMetaDataEmit2 :: ResetENCLog,](../metadata/imetadataemit2-resetenclog-method.md) pour préparer la session d’édition suivante.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="5d8ad-119">Le débogueur peut ensuite poursuivre le processus.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="5d8ad-120">Chaque fois que le débogueur appelle `ApplyChanges` sur un module qui a des métadonnées Delta, il doit également appeler [IMetaDataEmit :: ApplyEditAndContinue,](../metadata/imetadataemit-applyeditandcontinue-method.md) avec les mêmes métadonnées Delta sur toutes ses copies des métadonnées de ce module, à l’exception de la copie utilisée pour émettre les modifications.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="5d8ad-121">Si une copie des métadonnées n’est pas synchronisée avec les métadonnées réelles, le débogueur peut toujours lever cette copie et obtenir une nouvelle copie.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="5d8ad-122">Si la `ApplyChanges` méthode échoue, la session de débogage est dans un État non valide et doit être redémarrée.</span><span class="sxs-lookup"><span data-stu-id="5d8ad-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d8ad-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5d8ad-123">Requirements</span></span>  
 <span data-ttu-id="5d8ad-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d8ad-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d8ad-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d8ad-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d8ad-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d8ad-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d8ad-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d8ad-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
