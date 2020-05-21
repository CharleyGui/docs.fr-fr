---
title: Méthode ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762147"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a>Méthode ICLRStrongName::GetHashFromAssemblyFile
Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szFilePath`  
 dans Chemin d’accès au fichier à hacher.  
  
 `piHashAlg`  
 [in, out] Constante qui spécifie l’algorithme de hachage. Utilisez zéro pour l’algorithme de hachage par défaut.  
  
 `pbHash`  
 à Mémoire tampon de hachage retournée.  
  
 `cchHash`  
 dans Taille maximale demandée de `pbHash` .  
  
 `pchHash`  
 à Taille retournée, en octets, de `pbHash` .  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromAssemblyFileW, méthode](iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
