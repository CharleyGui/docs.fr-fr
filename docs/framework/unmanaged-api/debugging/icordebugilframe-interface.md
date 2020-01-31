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
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788582"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame, interface

Représente un frame de pile de code MSIL (Microsoft Intermediate Language). Cette interface est une sous-classe de l’interface ICorDebugFrame.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetIP, méthode](icordebugilframe-cansetip-method.md)|Obtient une valeur qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement d’offset spécifié.|  
|[EnumerateArguments, méthode](icordebugilframe-enumeratearguments-method.md)|Obtient un énumérateur pour les arguments dans ce frame.|  
|[EnumerateLocalVariables, méthode](icordebugilframe-enumeratelocalvariables-method.md)|Obtient un énumérateur pour les variables locales dans ce frame.|  
|[GetArgument, méthode](icordebugilframe-getargument-method.md)|Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL.|  
|[GetIP, méthode](icordebugilframe-getip-method.md)|Obtient la valeur du pointeur d’instruction et une valeur de combinaison au niveau du bit qui décrit comment la valeur du pointeur d’instruction a été obtenue.|  
|[GetLocalVariable, méthode](icordebugilframe-getlocalvariable-method.md)|Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL.|  
|[GetStackDepth, méthode](icordebugilframe-getstackdepth-method.md)|Non implémenté.|  
|[GetStackValue, méthode](icordebugilframe-getstackvalue-method.md)|Non implémenté.|  
|[SetIP, méthode](icordebugilframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement d’offset spécifié dans le code MSIL.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugILFrame` est une interface ICorDebugFrame spécialisée. Il est utilisé pour les frames de code MSIL ou pour les frames compilés juste-à-temps (JIT). Les frames compilés juste-à-temps implémentent à la fois l’interface `ICorDebugILFrame` et l’interface ICorDebugNativeFrame.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
