---
title: GetHashFromFileW, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771892"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW, fonction
Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.  
  
 Cette fonction a été déconseillée. Utilisez le [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) méthode à la place.  
  
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
 [in] Le nom Unicode du fichier à hacher.  
  
 `piHashAlg`  
 [in, out] L’algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par l’interface CryptoAPI Win32. Si `piHashAlg` est définie sur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 [out] Tableau d’octets contenant le hachage généré.  
  
 `cchHash`  
 [in] La taille maximale de la mémoire tampon vers laquelle pointe `pbHash`.  
  
 `pchHash`  
 [out] La taille, en octets, de `pbHash`.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est identique à [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), sauf que la spécification de nom de fichier est au format Unicode et non ANSI.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFileW, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
