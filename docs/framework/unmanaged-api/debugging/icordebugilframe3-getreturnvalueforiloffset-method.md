---
title: ICorDebugILFrame3::GetReturnValueForILOffset, méthode
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178813"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset, méthode
Obtient un objet "ICorDebugValue" qui résume la valeur de retour d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ILOffset`  
 L’IL compensé. Consultez la section Notes.  
  
 `ppReturnValue`  
 Un pointeur à l’adresse d’un objet d’interface "ICorDebugValue" qui fournit des informations sur la valeur de retour d’un appel de fonction.  
  
## <a name="remarks"></a>Notes   
 Cette méthode est utilisée avec la méthode [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour obtenir la valeur de retour d’une méthode. Il est particulièrement utile dans le cas de méthodes dont les valeurs de retour sont ignorées, comme dans les deux exemples de code suivants. Le premier exemple <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> appelle la méthode, mais ignore la valeur de retour de la méthode.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Le deuxième exemple illustre un problème beaucoup plus fréquent dans le débogage. Étant donné qu’une méthode est utilisée comme argument dans un appel de méthode, sa valeur de retour n’est accessible que lorsque le débbuggeur passe par la méthode appelée. Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, ce n’est pas possible.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Si vous passez la méthode [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) méthode un décalage IL à un site d’appel de fonction, il retourne un ou plusieurs décalages natifs. Le débbuggeur peut alors définir des points d’arrêt sur ces décalages indigènes dans la fonction. Lorsque le débbuggeur frappe l’un des points d’arrêt, vous pouvez alors passer le même décalage IL que vous avez passé à cette méthode pour obtenir la valeur de retour. Le débbuggeur doit alors effacer tous les points d’arrêt qu’il a fixés.  
  
> [!WARNING]
> La [méthode ICorDebugCode3::GetReturnValueLiveOffset Méthode](icordebugcode3-getreturnvalueliveoffset-method.md) et `ICorDebugILFrame3::GetReturnValueForILOffset` les méthodes vous permettent d’obtenir des informations de valeur de retour pour les types de référence seulement. La récupération des informations sur la valeur de retour provenant <xref:System.ValueType>de types de valeurs (c’est-à-dire tous les types qui dérivent) n’est pas prise en charge.  
  
 Le décalage IL `ILOffset` spécifié par le paramètre doit être à un site d’appel de fonction, et le débbuggee doit être arrêté à un point d’arrêt fixé à la compensation indigène retourné par [l’ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) méthode pour le même décalage IL. Si le débbuggee n’est pas arrêté à l’endroit correct pour le décalage IL spécifié, l’API échouera.  
  
 Si l’appel de fonction ne retourne pas une valeur, l’API échouera.  
  
 La `ICorDebugILFrame3::GetReturnValueForILOffset` méthode n’est disponible que sur les systèmes x86 et AMD64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetReturnValueLiveOffset, méthode](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3, interface](icordebugilframe3-interface.md)
