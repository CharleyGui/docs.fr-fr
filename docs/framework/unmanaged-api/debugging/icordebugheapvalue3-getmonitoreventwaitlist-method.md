---
title: ICorDebugHeapValue3::GetMonitorEventWaitList, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 21bf0122039a720ff8a1d38d62e77c2560dcc435
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726533"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList, méthode

Fournit une liste triée des threads mis en file d’attente sur l’événement associé à un verrou d’analyse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppThreadEnum`  
 à Énumérateur ICorDebugThreadEnum qui fournit la liste ordonnée de threads.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|The list is not empty.|  
|S_FALSE|La liste est vide.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarques  

 Le premier thread de la liste est le premier thread libéré par l’appel suivant à <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> . Le thread suivant de la liste est libéré sur l’appel suivant, et ainsi de suite.  
  
 Si la liste n’est pas vide, cette méthode retourne S_OK. Si la liste est vide, la méthode retourne S_FALSE ; dans ce cas, l’énumération est toujours valide, bien qu’elle soit vide.  
  
 Dans les deux cas, l’interface d’énumération est utilisable uniquement pour la durée de l’état synchronisé actuel. Toutefois, les interfaces du thread distantes sont valides jusqu’à ce que le thread se termine.  
  
 Si `ppThreadEnum` n’est pas un pointeur valide, le résultat n’est pas défini.  
  
 Si une erreur se produit et qu’il n’est pas possible de déterminer laquelle, le cas échéant, les threads attendent le moniteur, la méthode retourne un HRESULT qui indique un échec.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
