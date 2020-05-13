---
title: Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208622"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight

Accepte une chaîne de version common language runtime (CLR) retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante (en général, [ICorDebug](icordebug-interface.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `szDebuggeeVersion`\
 dans Chaîne de version du CLR dans le programme débogué cible, qui est retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md).  
  
 `ppCordb`\
 [out] Pointeur vers un autre pointeur vers un objet COM (`IUnknown`). Cet objet est casté en objet [ICorDebug](icordebug-interface.md) avant d’être retourné.  
  
## <a name="return-value"></a>Valeur de retour

 `S_OK`\
 `ppCordb`fait référence à un objet valide qui implémente l’interface d' [interface ICorDebug](icordebug-interface.md) .  
  
 `E_INVALIDARG`\
 `szDebuggeeVersion` ou `ppCordb` a la valeur null.  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 Un composant nécessaire pour le débogage CLR est introuvable. _Mscordbi. dll_ ou _mscordaccore. dll_ est introuvable dans le même répertoire que la cible CoreCLR. dll.  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 La version de mscordbi.dll ou de mscordaccore.dll n'est pas la même que celle du fichier CoreCLR.dll cible.  
  
 `E_FAIL`(ou autres `E_` codes de retour) \
 Impossible de retourner une [interface ICorDebug](icordebug-interface.md).  
  
## <a name="remarks"></a>Remarks

 L'interface retournée fournit les fonctionnalités permettant l'attachement à un CLR dans un processus cible et le débogage du code managé exécuté par le CLR.  
  
## <a name="requirements"></a>Spécifications

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** dbgshim. h  
  
 **Bibliothèque :** dbgshim. dll  
  
 **Versions de .NET Framework :** 3,5 SP1
