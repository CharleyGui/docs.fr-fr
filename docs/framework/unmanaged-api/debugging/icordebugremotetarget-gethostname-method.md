---
title: ICorDebugRemoteTarget::GetHostName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: 3e946d8a27ec6b568b2f3c3633695c9f6795c938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712051"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName, méthode

Retourne le nom de domaine complet ou l’adresse IPv4 de l’ordinateur cible de débogage distant. IPV6 n’est pas pris en charge pour l’instant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Paramètres  

 `cchHostName`  
 dans Taille, en caractères, de la `szHostName` mémoire tampon. Si ce paramètre a la valeur 0 (zéro), `szHostName` doit avoir la valeur null.  
  
 `pcchHostName`  
 à Nombre de caractères, y compris la marque de fin null, dans le nom d’hôte ou l’adresse IP. Ce paramètre peut avoir la valeur Null.  
  
 `szHostName`  
 à Mémoire tampon qui contient le nom d’hôte ou l’adresse IP.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK  
 Le nom d’hôte ou l’adresse IP a été retourné avec succès.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de retourner le nom d’hôte ou l’adresse IP.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode est implémentée par l’enregistreur du débogueur. Il doit suivre le paradigme d’appel multiple : lors du premier appel, l’appelant passe NULL à et à et `cchHostName` `szHostName` , et `pcchHostName` retourne la taille de la mémoire tampon requise. Lors du deuxième appel, la taille précédemment retournée est passée `cchHostName` , et une mémoire tampon de taille appropriée est passée `szHostName` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 3,5 SP1  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRemoteTarget, interface](icordebugremotetarget-interface.md)
- [ICorDebug, interface](icordebug-interface.md)
