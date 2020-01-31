---
title: ICorDebugCode3::GetReturnValueLiveOffset, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: dc03365b72a5f3613402faf1aed44b5683e9892c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777838"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset, méthode
Pour un offset IL spécifié, obtient les offsets natifs où un point d’arrêt doit être placé afin que le débogueur puisse obtenir la valeur de retour d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ILoffset`  
 Offset IL. Il doit s’agir d’un site d’appel de fonction, sinon l’appel de fonction échoue.  
  
 `bufferSize`  
 Nombre d’octets disponibles pour stocker des `pOffsets`.  
  
 `pFetched`  
 Pointeur vers le nombre d’offsets réellement retournés. En règle générale, sa valeur est 1, mais une instruction IL unique peut être mappée à plusieurs instructions `CALL` assembly.  
  
 `pOffsets`  
 Tableau d’offsets natifs. En règle générale, `pOffsets` contient un offset unique, bien qu’une seule instruction IL puisse être mappée à plusieurs instructions d’assembly `CALL`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée avec la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour d’une méthode qui retourne un type référence. Le passage d’un offset IL à un site d’appel de fonction à cette méthode retourne un ou plusieurs offsets natifs. Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction. Quand le débogueur atteint l’un des points d’arrêt, vous pouvez ensuite passer le même offset IL que celui que vous avez passé à cette méthode à la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour. Le débogueur doit ensuite effacer tous les points d’arrêt qu’il définit.  
  
> [!WARNING]
> Les méthodes `ICorDebugCode3::GetReturnValueLiveOffset` et [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) vous permettent d’obtenir des informations de valeur de retour pour les types référence uniquement. La récupération d’informations de valeur de retour à partir de types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas prise en charge.  
  
 La fonction retourne les valeurs de `HRESULT` indiquées dans le tableau suivant.  
  
|Valeur de `HRESULT`|Description|  
|---------------------|-----------------|  
|`S_OK`|Opération réussie.|  
|`CORDBG_E_INVALID_OPCODE`|Le site de décalage IL donné n’est pas une instruction d’appel, ou la fonction retourne `void`.|  
|`CORDBG_E_UNSUPPORTED`|L’offset IL donné est un appel approprié, mais le type de retour n’est pas pris en charge pour l’obtention d’une valeur de retour.|  
  
 La méthode `ICorDebugCode3::GetReturnValueLiveOffset` est disponible uniquement sur les systèmes x86 et AMD64.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetReturnValueForILOffset, méthode](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3, interface](icordebugcode3-interface.md)
