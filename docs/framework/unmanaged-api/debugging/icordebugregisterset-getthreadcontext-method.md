---
title: ICorDebugRegisterSet::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: 04ae3c4dd663351eaf1a58646e24e8ae95aeb9ad
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378284"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext, méthode
Obtient le contexte du thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `contextSize`  
 dans Taille, en octets, du `context` tableau.  
  
 `context`  
 [in, out] Tableau d’octets qui composent la `CONTEXT` structure Win32 pour la plateforme actuelle.  
  
## <a name="remarks"></a>Remarks  
 Le débogueur doit appeler cette fonction au lieu de la `GetThreadContext` fonction Win32, car le thread peut être dans un État « détourné » dans lequel son contexte a été modifié temporairement. Les données retournées sont une `CONTEXT` structure Win32 pour la plateforme actuelle.  
  
 Pour les frames non-feuilles, les clients doivent vérifier quels registres sont valides à l’aide de [ICorDebugRegisterSet :: GetRegistersAvailable,](icordebugregisterset-getregistersavailable-method.md).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
