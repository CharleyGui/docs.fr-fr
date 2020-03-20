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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175081"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW, fonction
Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) à la place.  
  
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
  
## <a name="remarks"></a>Notes   
 Cette fonction est la même que [GetHashFromFile](gethashfromfile-function.md), sauf que la spécification nom de fichier est Unicode au lieu de ANSI.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFileW, méthode](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, méthode](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
