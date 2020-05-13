---
title: ICorDebugThread, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379818"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interface
Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearCurrentException, méthode](icordebugthread-clearcurrentexception-method.md)|Cette méthode n’est pas implémentée. Ne pas l'utiliser.|  
|[CreateEval, méthode](icordebugthread-createeval-method.md)|Crée un objet ICorDebugEval qui fonctionne sur ce `ICorDebugThread` .|  
|[CreateStepper, méthode](icordebugthread-createstepper-method.md)|Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé dans le frame actif dans ce `ICorDebugThread` .|  
|[EnumerateChains, méthode](icordebugthread-enumeratechains-method.md)|Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile dans ce `ICorDebugThread` .|  
|[GetActiveChain, méthode](icordebugthread-getactivechain-method.md)|Obtient un pointeur d’interface vers l’ICorDebugChain actif sur ce `ICorDebugThread` .|  
|[GetActiveFrame, méthode](icordebugthread-getactiveframe-method.md)|Obtient un pointeur d’interface vers le ICorDebugFrame actif sur ce `ICorDebugThread` .|  
|[GetAppDomain, méthode](icordebugthread-getappdomain-method.md)|Obtient un pointeur d’interface vers le domaine d’application dans lequel ce est actuellement en cours d' `ICorDebugThread` exécution.|  
|[GetCurrentException, méthode](icordebugthread-getcurrentexception-method.md)|Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.|  
|[GetDebugState, méthode](icordebugthread-getdebugstate-method.md)|Obtient une valeur CorDebugThreadState qui décrit l’état de débogage actuel de ce `ICorDebugThread` .|  
|[GetHandle, méthode](icordebugthread-gethandle-method.md)|Obtient le handle actuel pour la partie active de ce `ICorDebugThread` .|  
|[GetID, méthode](icordebugthread-getid-method.md)|Obtient l’identificateur de système d’exploitation actuel de la partie active de ce `ICorDebugThread` .|  
|[GetObject, méthode](icordebugthread-getobject-method.md)|Obtient un pointeur d’interface vers le thread common language runtime (CLR).|  
|[GetProcess, méthode](icordebugthread-getprocess-method.md)|Obtient un pointeur d’interface vers le processus dont se `ICorDebugThread` forme un composant.|  
|[GetRegisterSet, méthode](icordebugthread-getregisterset-method.md)|Obtient un pointeur d’interface vers le jeu de registres associé à ce `ICorDebugThread` .|  
|[GetUserState, méthode](icordebugthread-getuserstate-method.md)|Obtient une combinaison d’opérations de bits de valeurs CorDebugUserState, qui décrivent l’état actuel de ce `ICorDebugThread` .|  
|[SetDebugState, méthode](icordebugthread-setdebugstate-method.md)|Définit une combinaison d’opérations de bits de `CorDebugThreadState` valeurs qui décrivent l’état de débogage de ce `ICorDebugThread` .|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
