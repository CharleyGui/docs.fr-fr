---
title: ICorDebugILFrame4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: d0b1c31d45efea4892182c43c801112530361994
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213700"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4, interface
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire. Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx, méthode](icordebugilframe4-enumeratelocalvariablesex-method.md)|Retourne une liste des variables locales disponibles dans le frame actif.|  
|[GetCodeEx, méthode](icordebugilframe4-getcodeex-method.md)|Retourne le code exécuté par ce frame de pile.|  
|[GetLocalVariableEx, méthode](icordebugilframe4-getlocalvariableex-method.md)|Retourne la valeur d'une variable locale du frame de langage intermédiaire.|  
  
## <a name="remarks"></a>Remarks  
 Ces méthodes offrent des fonctionnalités en plus de celles fournies par les méthodes [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)et [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) . Chaque méthode comprend un paramètre `flags` qui spécifie si des variables locales ou du code supplémentaires définis par une demande ReJIT du profileur sont visibles.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
