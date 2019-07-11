---
title: ICorDebugMetaDataLocator::GetMetaData, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b761d31e640063e11c1e549966bb372449fe743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762272"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData, méthode
Indique au débogueur de retourner le chemin d’accès complet à un module dont les métadonnées sont nécessaires pour effectuer une opération demandée par le débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszImagePath`  
 [in] Chaîne terminée par le caractère null qui représente le chemin d’accès complet au fichier. Si le chemin d’accès complet n’est pas disponible, le nom et l’extension du fichier (*filename*. *extension*).  
  
 `dwImageTimeStamp`  
 [in] Horodatage des en-têtes de fichier PE de l'image. Ce paramètre peut potentiellement être utilisé pour un serveur de symboles ([SymSrv](/windows/desktop/debug/using-symsrv)) recherche.  
  
 `dwImageSize`  
 [in] Taille d'image dans les en-têtes de fichier PE. Ce paramètre peut potentiellement être utilisé pour une recherche SymSrv.  
  
 `cchPathBuffer`  
 [in] Nombre de caractères dans `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Nombre de `WCHAR` écrits dans `wszPathBuffer`.  
  
 Si la méthode retourne E_NOT_SUFFICIENT_BUFFER, contient le nombre de `WCHAR` nécessaires pour stocker le chemin d'accès.  
  
 `wszPathBuffer`  
 [out] Pointeur vers une mémoire tampon dans laquelle le débogueur copie le chemin d’accès complet du fichier contenant les métadonnées demandées.  
  
 Le `ofReadOnly` indicateur à partir de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération est utilisée pour demander l’accès en lecture seule aux métadonnées dans ce fichier.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode. Tous les autres HRESULT d'échec indiquent que le fichier n'est pas récupérable.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée. `wszPathBuffer` contient le chemin d'accès complet au fichier et se termine par le caractère null.|  
|E_NOT_SUFFICIENT_BUFFER|La taille actuelle de `wszPathBuffer` n’est pas suffisante pour contenir le chemin d’accès complet. Dans ce cas, `pcchPathBuffer` contient le nombre nécessaire de `WCHAR`, y compris le caractère null de fin, et la méthode `GetMetaData` est appelée une deuxième fois avec la taille de mémoire tampon demandée.|  
  
## <a name="remarks"></a>Notes  
 Si `wszImagePath` contient le chemin d’accès complet d’un module dans un dump, il spécifie le chemin d’accès de l’ordinateur sur lequel le dump a été collecté. Le fichier n'existe peut-être pas à cet emplacement ou un fichier incorrect portant le même nom peut être stocké dans le chemin d'accès.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugThread4, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
