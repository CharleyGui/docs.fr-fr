---
title: Méthode ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176368"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>Méthode ICLRStrongName::GetHashFromFileW
Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [dans] Le nom Unicode du fichier au hachage.  
  
 `piHashAlg`  
 [dans, dehors] L’algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par le CryptoAPI Win32. Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 [out] Un tableau d’en-lieu contenant le hachage généré.  
  
 `cchHash`  
 [dans] La taille maximale de la `pbHash`mémoire tampon indiquée par .  
  
 `pchHash`  
 [out] La taille, dans les `pbHash`octets, de .  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes   
 Cette méthode est la même que la méthode [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) méthode, sauf que la spécification nom de fichier est Unicode au lieu de ANSI.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MetaHost.h MetaHost.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
