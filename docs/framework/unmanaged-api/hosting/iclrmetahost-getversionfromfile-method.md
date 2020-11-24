---
title: ICLRMetaHost::GetVersionFromFile, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: f5e0ead41ebd13c259c24fa0c02bcc9a3b33e0fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689444"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile, méthode

Obtient la version de compilation .NET Framework d’origine d’un assembly (stockée dans les métadonnées), en fonction de son chemin d’accès au fichier. Cette méthode remplace la fonction [GetFileVersion,](getfileversion-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pwzFilePath`  
 dans Chemin d’accès complet au fichier d’assembly.  
  
 `pwzbuffer`  
 à Version de compilation .NET Framework stockée dans les métadonnées, au format «v *A*. *B*[.*X*]». *A*, *B* et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build. La longueur de cette chaîne est limitée à MAX_PATH.  
  
> [!NOTE]
> Cette sortie correspond au nom du répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.  
  
 Les exemples de valeurs sont « v 1.0.3705 », « v 1.1.4322 », « v 2.0.50727 » et « v 4.0 ». *X*», où *x* dépend du numéro de Build installé. Notez que le préfixe « v » est obligatoire.  
  
 `pcchBuffer`  
 [in, out] Taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzbuffer` ou `pcchBuffer` est null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|La mémoire tampon est insuffisante.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](iclrmetahost-interface.md)
- [Hébergement](index.md)
