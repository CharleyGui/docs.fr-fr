---
title: ICorDebugThread::EnumerateChains, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771101"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains, méthode
Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile dans cet objet ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppChains`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugChainEnum` objet qui permet l’énumération de la pile de toutes les chaînes dans ce thread, en commençant par la chaîne active (autrement dit, la plus récente).  
  
## <a name="remarks"></a>Notes  
 La chaîne de pile représente la pile des appels physique pour le thread. Les circonstances suivantes créer une limite de chaîne de pile :  
  
- Une transition managé à managé ou non managé à managé.  
  
- Un changement de contexte.  
  
- Un blocage d’un thread de l’utilisateur du débogueur.  
  
 Dans le cas simple pour un thread qui est en cours d’exécution du code purement managé dans un contexte unique, une correspondance exacte existe entre les threads et les chaînes de pile.  
  
 Un débogueur peut être amené à réorganiser les piles des appels physique de tous les threads dans les piles des appels logiques. Il serait nécessaire de trier des chaînes de tous les threads en fonction de leurs relations appelant/appelé et le regroupement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
