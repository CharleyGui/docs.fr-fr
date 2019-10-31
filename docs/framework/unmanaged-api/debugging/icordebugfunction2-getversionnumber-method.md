---
title: ICorDebugFunction2::GetVersionNumber, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137803"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber, méthode
Obtient la version modifier & continuer de cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pnVersion`  
 à Pointeur vers un entier qui est le numéro de version de la fonction représentée par cet objet ICorDebugFunction2.  
  
## <a name="remarks"></a>Notes  
 Le Runtime effectue le suivi du nombre de modifications apportées à chaque module pendant une session de débogage. Le numéro de version d’une fonction est un nombre de fois supérieur au numéro de la modification qui a introduit la fonction. La version d’origine de la fonction est la version 1. Le nombre est incrémenté pour un module chaque fois que [ICorDebugModule2 :: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) est appelé sur ce module. Ainsi, si le corps d’une fonction a été remplacé dans le premier et le troisième appel à `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` peut retourner la version 1, 2 ou 4 pour cette fonction, mais pas la version 3. (Cette fonction n’aurait pas de version 3.)  
  
 Le numéro de version est suivi séparément pour chaque module. Par conséquent, si vous effectuez quatre modifications sur le module 1 et aucune sur le module 2, la modification suivante du module 1 affecte un numéro de version 6 à toutes les fonctions modifiées dans le module 1. Si la même modification touche le module 2, les fonctions du module 2 obtiennent le numéro de version 2.  
  
 Le numéro de version obtenu par la méthode `GetVersionNumber` peut être inférieur à celui obtenu par [ICorDebugFunction :: GetCurrentVersionNumber,](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 La méthode [ICorDebugCode :: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) effectue la même opération que `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
