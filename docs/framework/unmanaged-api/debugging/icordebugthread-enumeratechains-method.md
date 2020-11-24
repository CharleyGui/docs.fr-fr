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
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688183"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains, méthode

Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile de cet objet ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppChains`  
 à Pointeur vers l’adresse d’un `ICorDebugChainEnum` objet qui autorise l’énumération de toutes les chaînes de pile dans ce thread, en commençant à la chaîne active (autrement dit, la plus récente).  
  
## <a name="remarks"></a>Remarques  

 La chaîne de pile représente la pile d’appels physique du thread. Les circonstances suivantes créent une limite de chaîne de pile :  
  
- Transition managée vers non managée ou non managée vers managée.  
  
- Commutateur de contexte.  
  
- Détournement d’un thread utilisateur par le débogueur.  
  
 Dans le cas simple d’un thread qui exécute du code purement managé dans un contexte unique, une correspondance un-à-un existe entre les threads et les chaînes de pile.  
  
 Un débogueur peut réorganiser les piles des appels physiques de tous les threads en piles d’appels logiques. Cela implique de trier toutes les chaînes des threads en fonction de leurs relations appelant/appelé, puis de les regrouper.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
