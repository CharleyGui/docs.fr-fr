---
title: ICorDebugILFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917020"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame, interface

Représente un frame de pile de code MSIL (Microsoft Intermediate Language). Cette interface est une sous-classe de l’interface ICorDebugFrame.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié.|  
|[EnumerateArguments, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Obtient un énumérateur pour les arguments dans ce frame.|  
|[EnumerateLocalVariables, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Obtient un énumérateur pour les variables locales dans ce frame.|  
|[GetArgument, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL.|  
|[GetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Obtient la valeur du pointeur d’instruction et une valeur de combinaison au niveau du bit qui décrit comment la valeur du pointeur d’instruction a été obtenue.|  
|[GetLocalVariable, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL.|  
|[GetStackDepth, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Non implémenté.|  
|[GetStackValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Non implémenté.|  
|[SetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement d’offset spécifié dans le code MSIL.|  
  
## <a name="remarks"></a>Notes  
 L' `ICorDebugILFrame` interface est une interface ICorDebugFrame spécialisée. Il est utilisé pour les frames de code MSIL ou pour les frames compilés juste-à-temps (JIT). Les frames compilés juste-à `ICorDebugILFrame` -temps implémentent à la fois l’interface et l’interface ICorDebugNativeFrame.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
