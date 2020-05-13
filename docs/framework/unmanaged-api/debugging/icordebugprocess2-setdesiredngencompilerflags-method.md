---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 366a48e5f6abd92f0c6f796f40bdd263181da4a8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213476"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode
Définit les indicateurs qui doivent être incorporés dans une image précompilée pour permettre au runtime de charger cette image dans le processus en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwFlags`  
 dans Valeur de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) qui spécifie les indicateurs de compilateur utilisés pour sélectionner l’image précompilée correcte.  
  
## <a name="remarks"></a>Remarks  
 La `SetDesiredNGENCompilerFlags` méthode spécifie les indicateurs qui doivent être incorporés dans une image précompilée afin que le runtime charge cette image dans ce processus. Les indicateurs définis par cette méthode sont utilisés uniquement pour sélectionner l’image précompilée correcte. Si aucune image de ce type n’existe, le runtime chargera à la place l’image MSIL (Microsoft Intermediate Language) et le compilateur juste-à-temps (JIT). Dans ce cas, le débogueur doit toujours utiliser la méthode [ICorDebugModule2 :: SetJITCompilerFlags,](icordebugmodule2-setjitcompilerflags-method.md) pour définir les indicateurs comme vous le souhaitez pour la compilation JIT.  
  
 Si une image est chargée, mais que certaines compilations JIT doivent avoir lieu pour cette image (ce qui sera le cas si l’image contient des génériques), les indicateurs de compilateur spécifiés par la `SetDesiredNGENCompilerFlags` méthode s’appliqueront à la compilation JIT supplémentaire.  
  
 La `SetDesiredNGENCompilerFlags` méthode doit être appelée pendant le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . Toute tentative d’appel de la `SetDesiredNGENCompilerFlags` méthode échoue. En outre, les tentatives de définition d’indicateurs qui ne sont pas définis dans l' `CorDebugJITCompilerFlags` énumération ou qui ne sont pas autorisés pour le processus donné échouent.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
