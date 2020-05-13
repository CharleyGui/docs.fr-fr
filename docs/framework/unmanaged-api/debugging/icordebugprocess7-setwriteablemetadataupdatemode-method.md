---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212254"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="51362-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode</span><span class="sxs-lookup"><span data-stu-id="51362-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="51362-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="51362-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="51362-104">Configure la façon dont le débogueur gère les mises à jour en mémoire des métadonnées dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="51362-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51362-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51362-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51362-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51362-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="51362-107">Valeur d’énumération [writeablemetadataupdatemode,](writeablemetadataupdatemode-enumeration.md) qui spécifie si les mises à jour en mémoire des métadonnées dans le processus cible sont visibles ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ou non visibles ( `WriteableMetadataUpdateMode::LegacyCompatPolicy` ) vers le débogueur.</span><span class="sxs-lookup"><span data-stu-id="51362-107">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51362-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="51362-108">Remarks</span></span>  
 <span data-ttu-id="51362-109">Les mises à jour apportées aux métadonnées du processus cible peuvent provenir de Modifier et continuer, d'un profileur ou de <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51362-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51362-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="51362-110">Requirements</span></span>  
 <span data-ttu-id="51362-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51362-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51362-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51362-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51362-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51362-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51362-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51362-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51362-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51362-115">See also</span></span>

- [<span data-ttu-id="51362-116">ICorDebugProcess7, interface</span><span class="sxs-lookup"><span data-stu-id="51362-116">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="51362-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="51362-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
