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
ms.openlocfilehash: a6b1a7c9be821890a3f15d8c3297273607f5bedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709698"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges, méthode

Applique les modifications apportées aux métadonnées et les modifications apportées au code MSIL (Microsoft Intermediate Language) au processus en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cbMetadata`  
 dans Taille, en octets, des métadonnées Delta.  
  
 `pbMetadata`  
 dans Mémoire tampon qui contient les métadonnées Delta. L’adresse de la mémoire tampon est retournée à partir de la méthode [IMetaDataEmit2 :: SaveDeltaToMemory,](../metadata/imetadataemit2-savedeltatomemory-method.md) .  
  
 Les adresses virtuelles relatives (RVA) dans les métadonnées doivent être relatives au début du code MSIL.  
  
 `cbIL`  
 dans Taille, en octets, du code MSIL Delta.  
  
 `pbIL`  
 dans Mémoire tampon qui contient le code MSIL mis à jour.  
  
## <a name="remarks"></a>Remarques  

 Le `pbMetadata` paramètre est dans un format de métadonnées Delta spécial (comme sortie par [IMetaDataEmit2 :: SaveDeltaToMemory,](../metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` prend les métadonnées précédentes comme base et décrit les modifications individuelles à appliquer à cette base.  
  
 En revanche, le `pbIL[` paramètre] contient le nouveau MSIL pour la méthode mise à jour et est destiné à remplacer complètement le code MSIL précédent pour cette méthode.  
  
 Lorsque le MSIL Delta et les métadonnées ont été créés dans la mémoire du débogueur, le débogueur appelle `ApplyChanges` pour envoyer les modifications dans le Common Language Runtime (CLR). Le Runtime met à jour ses tables de métadonnées, place le nouveau MSIL dans le processus et configure une compilation juste-à-temps (JIT) du nouveau MSIL. Lorsque les modifications ont été appliquées, le débogueur doit appeler [IMetaDataEmit2 :: ResetENCLog,](../metadata/imetadataemit2-resetenclog-method.md) pour préparer la session d’édition suivante. Le débogueur peut ensuite poursuivre le processus.  
  
 Chaque fois que le débogueur appelle `ApplyChanges` sur un module qui a des métadonnées Delta, il doit également appeler [IMetaDataEmit :: ApplyEditAndContinue,](../metadata/imetadataemit-applyeditandcontinue-method.md) avec les mêmes métadonnées Delta sur toutes ses copies des métadonnées de ce module, à l’exception de la copie utilisée pour émettre les modifications. Si une copie des métadonnées n’est pas synchronisée avec les métadonnées réelles, le débogueur peut toujours lever cette copie et obtenir une nouvelle copie.  
  
 Si la `ApplyChanges` méthode échoue, la session de débogage est dans un État non valide et doit être redémarrée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
