---
title: Méthode ICLRStrongName::StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: f08006c532d2778de67a4bab09623d248362535c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937429"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>Méthode ICLRStrongName::StrongNameTokenFromAssemblyEx
Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique que le jeton représente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `wszFilePath`  
 dans Chemin d’accès au fichier exécutable portable (PE) pour l’assembly.  
  
 `ppbStrongNameToken`  
 à Jeton de nom fort retourné.  
  
 `pcbStrongNameToken`  
 à Taille, en octets, du jeton de nom fort.  
  
 `ppbPublicKeyBlob`  
 à Clé publique retournée.  
  
 `pcbPublicKeyBlob`  
 à Taille, en octets, de la clé publique.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes  
 Un jeton de nom fort est la forme raccourcie d’une clé publique. Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly. Le jeton fait partie du nom fort de l’assembly et peut être lu à partir des métadonnées de l’assembly.  
  
 Une fois la clé récupérée et le jeton créé, vous devez appeler la méthode [ICLRStrongName :: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pour libérer la mémoire allouée.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromAssembly, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
