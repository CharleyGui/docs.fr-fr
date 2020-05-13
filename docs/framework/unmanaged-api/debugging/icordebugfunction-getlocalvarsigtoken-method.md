---
title: ICorDebugFunction::GetLocalVarSigToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
ms.openlocfilehash: a923701b05f7d283c4fd464d470fb0c9243c1bd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213606"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a>ICorDebugFunction::GetLocalVarSigToken, méthode
Obtient le jeton de métadonnées pour la signature de variable locale de la fonction qui est représentée par cette instance ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pmdSig`  
 à Pointeur vers le `mdSignature` jeton pour la signature de variable locale de cette fonction, ou `mdSignatureNil` , si cette fonction n’a pas de variables locales.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
