---
title: ICorDebugProcess6, interface
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 4ad350e36ee15d7c1781e03698fbee3fd40c4c12
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212865"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6, interface
Étend logiquement l’interface ICorDebugProcess pour activer des fonctionnalités telles que le fractionnement de module virtuel ou le décodage des événements de débogage managés qui sont codés dans des événements de débogage d’exception native.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DecodeEvent, méthode](icordebugprocess6-decodeevent-method.md)|Décode les événements de débogage managés qui ont été encapsulés dans la charge utile des événements de débogage d'exception native conçus à cet effet.|  
|[EnableVirtualModuleSplitting, méthode](icordebugprocess6-enablevirtualmodulesplitting-method.md)|Active ou désactive le fractionnement de module virtuel.|  
|[GetCode, méthode](icordebugprocess6-getcode-method.md)|Obtient des informations sur le code managé à une adresse de code particulière.|  
|[GetExportStepInfo, méthode](icordebugprocess6-getexportstepinfo-method.md)|Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.|  
|[MarkDebuggerAttached, méthode](icordebugprocess6-markdebuggerattached-method.md)|Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.|  
|[ProcessStateChanged, méthode](icordebugprocess6-processstatechanged-method.md)|Informe [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> L'interface est uniquement disponible avec .NET Native. Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
