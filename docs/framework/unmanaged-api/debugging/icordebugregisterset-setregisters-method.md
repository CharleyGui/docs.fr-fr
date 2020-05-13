---
title: ICorDebugRegisterSet::SetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: eba86c09197aad6bac284c52fe164432e197c6f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378261"
---
# <a name="icordebugregistersetsetregisters-method"></a>ICorDebugRegisterSet::SetRegisters, méthode
`SetRegisters`n’est pas implémenté dans la version 2,0 de .NET Framework. N'appelez pas cette méthode.  
  
> [!NOTE]
> Utilisez les opérations de niveau supérieur telles que [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md) ou [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
