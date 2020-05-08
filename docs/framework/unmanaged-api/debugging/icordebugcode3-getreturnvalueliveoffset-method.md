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
ms.openlocfilehash: 2cb4c79601061ab8473d6d7ca50c4ed2f92b01c4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893426"
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
  
## <a name="parameters"></a>Paramètres  
 `ILoffset`  
 Offset IL. Il doit s’agir d’un site d’appel de fonction, sinon l’appel de fonction échoue.  
  
 `bufferSize`  
 Nombre d’octets disponibles pour le stockage `pOffsets`.  
  
 `pFetched`  
 Pointeur vers le nombre d’offsets réellement retournés. En règle générale, sa valeur est 1, mais une instruction IL unique peut être `CALL` mappée à plusieurs instructions d’assembly.  
  
 `pOffsets`  
 Tableau d’offsets natifs. En général `pOffsets` , contient un offset unique, bien qu’une seule instruction il puisse être mappée à `CALL` plusieurs instructions d’assembly.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est utilisée avec la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour d’une méthode qui retourne un type référence. Le passage d’un offset IL à un site d’appel de fonction à cette méthode retourne un ou plusieurs offsets natifs. Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction. Quand le débogueur atteint l’un des points d’arrêt, vous pouvez ensuite passer le même offset IL que celui que vous avez passé à cette méthode à la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour. Le débogueur doit ensuite effacer tous les points d’arrêt qu’il définit.  
  
> [!WARNING]
> Les `ICorDebugCode3::GetReturnValueLiveOffset` méthodes et [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) vous permettent d’obtenir des informations de valeur de retour pour les types référence uniquement. La récupération des informations de valeur de retour à partir des types valeur (autrement dit, <xref:System.ValueType>tous les types qui dérivent de) n’est pas prise en charge.  
  
 La fonction retourne les `HRESULT` valeurs indiquées dans le tableau suivant.  
  
|Valeur `HRESULT`|Description|  
|---------------------|-----------------|  
|`S_OK`|Opération réussie.|  
|`CORDBG_E_INVALID_OPCODE`|Le site de décalage IL donné n’est pas une instruction d’appel, ou `void`la fonction retourne.|  
|`CORDBG_E_UNSUPPORTED`|L’offset IL donné est un appel approprié, mais le type de retour n’est pas pris en charge pour l’obtention d’une valeur de retour.|  
  
 La `ICorDebugCode3::GetReturnValueLiveOffset` méthode est disponible uniquement sur les systèmes x86 et amd64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetReturnValueForILOffset, méthode](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3, interface](icordebugcode3-interface.md)
