---
title: Méthode ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: e4a5f6440a016176cf06704b342c173b29748e78
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762108"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>Méthode ICLRStrongName::GetHashFromFile
Génère un hachage sur le contenu du fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szFilePath`  
 dans Nom du fichier à hacher.  
  
 `piHashAlg`  
 [in, out] Algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par l’CryptoAPI Win32. Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 à Tableau d’octets contenant le hachage généré.  
  
 `cchHash`  
 dans Taille maximale de la mémoire tampon `pbHash` vers laquelle pointe.  
  
 `pchHash`  
 à Taille, en octets, du retourné `pbHash` .  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Notes  
 Cette méthode est la même que la méthode [ICLRStrongName :: GetHashFromFileW (](iclrstrongname-gethashfromfilew-method.md) , à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFileW, méthode](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
