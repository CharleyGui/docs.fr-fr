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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178938"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset, méthode
Pour un décalage IL spécifié, obtient les décalages natifs où un point d’arrêt doit être placé de sorte que le débbuggeur peut obtenir la valeur de retour d’une fonction.  
  
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
 L’IL compensé. Il doit s’agir d’un site d’appel de fonction ou l’appel de fonction échouera.  
  
 `bufferSize`  
 Le nombre d’octets `pOffsets`disponibles pour stocker .  
  
 `pFetched`  
 Un pointeur sur le nombre de compensations effectivement retourné. Habituellement, sa valeur est de 1, mais `CALL` une seule instruction IL peut cartographier à plusieurs instructions d’assemblage.  
  
 `pOffsets`  
 Un éventail de décalages indigènes. Typiquement, `pOffsets` contient un décalage unique, bien qu’une seule `CALL` instruction d’IL puisse cartographier à plusieurs instructions d’assemblage.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est utilisée avec la méthode [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour d’une méthode qui renvoie un type de référence. Le passage d’un décalage IL à un site d’appel de fonction à cette méthode renvoie un ou plusieurs décalages indigènes. Le débbuggeur peut alors définir des points d’arrêt sur ces décalages indigènes dans la fonction. Lorsque le débbuggeur frappe l’un des points d’arrêt, vous pouvez alors passer le même décalage IL que vous avez passé à cette méthode à [l’ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour. Le débbuggeur doit alors effacer tous les points d’arrêt qu’il a fixés.  
  
> [!WARNING]
> Les `ICorDebugCode3::GetReturnValueLiveOffset` méthodes et [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) vous permettent d’obtenir des informations de valeur de retour pour les types de référence seulement. La récupération des informations sur la valeur de retour provenant <xref:System.ValueType>de types de valeurs (c’est-à-dire tous les types qui dérivent) n’est pas prise en charge.  
  
 La fonction `HRESULT` renvoie les valeurs indiquées dans le tableau suivant.  
  
|Valeur `HRESULT`|Description|  
|---------------------|-----------------|  
|`S_OK`|Réussite.|  
|`CORDBG_E_INVALID_OPCODE`|Le site de compensation IL donné n’est `void`pas une instruction d’appel, ou la fonction revient .|  
|`CORDBG_E_UNSUPPORTED`|Le décalage DONNÉ IL est un appel approprié, mais le type de retour n’est pas pris en compte pour obtenir une valeur de retour.|  
  
 La `ICorDebugCode3::GetReturnValueLiveOffset` méthode n’est disponible que sur les systèmes x86 et AMD64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetReturnValueForILOffset, méthode](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3, interface](icordebugcode3-interface.md)
