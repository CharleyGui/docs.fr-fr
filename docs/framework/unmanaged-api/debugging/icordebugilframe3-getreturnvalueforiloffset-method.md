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
ms.openlocfilehash: 7a96385ccc6e7f9089365c19bb8f150015bba81c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788528"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset, méthode
Obtient un objet « ICorDebugValue » qui encapsule la valeur de retour d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ILOffset`  
 Offset IL. Consultez la section Notes.  
  
 `ppReturnValue`  
 Pointeur vers l’adresse d’un objet d’interface « ICorDebugValue » qui fournit des informations sur la valeur de retour d’un appel de fonction.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée avec la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour obtenir la valeur de retour d’une méthode. Elle est particulièrement utile dans le cas des méthodes dont les valeurs de retour sont ignorées, comme dans les deux exemples de code suivants. Le premier exemple appelle la méthode <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, mais ignore la valeur de retour de la méthode.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Le deuxième exemple illustre un problème bien plus courant lors du débogage. Étant donné qu’une méthode est utilisée en tant qu’argument dans un appel de méthode, sa valeur de retour est accessible uniquement lorsque le débogueur parcourt la méthode appelée. Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, ce n’est pas possible.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Si vous transmettez à la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) un offset il à un site d’appel de fonction, elle retourne un ou plusieurs offsets natifs. Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction. Quand le débogueur atteint l’un des points d’arrêt, vous pouvez ensuite passer le même offset IL que celui que vous avez passé à cette méthode pour obtenir la valeur de retour. Le débogueur doit ensuite effacer tous les points d’arrêt qu’il définit.  
  
> [!WARNING]
> La [méthode ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) et les méthodes `ICorDebugILFrame3::GetReturnValueForILOffset` vous permettent d’obtenir des informations de valeur de retour pour les types référence uniquement. La récupération d’informations de valeur de retour à partir de types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas prise en charge.  
  
 Le décalage IL spécifié par le paramètre `ILOffset` doit se trouver sur un site d’appel de fonction, et l’élément débogué doit être arrêté à un point d’arrêt défini au niveau de l’offset natif retourné par la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour le même offset il. Si le programme débogué n’est pas arrêté à l’emplacement approprié pour l’offset IL spécifié, l’API échoue.  
  
 Si l’appel de fonction ne retourne pas de valeur, l’API échoue.  
  
 La méthode `ICorDebugILFrame3::GetReturnValueForILOffset` est disponible uniquement sur les systèmes x86 et AMD64.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetReturnValueLiveOffset, méthode](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3, interface](icordebugilframe3-interface.md)
