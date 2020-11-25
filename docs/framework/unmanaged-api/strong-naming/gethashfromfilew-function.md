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
ms.openlocfilehash: 8038d0abc93e058e6bde897bbf2261d8f1df885a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732318"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW, fonction

Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: GetHashFromFileW (](../hosting/iclrstrongname-gethashfromfilew-method.md) à la place.  
  
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
 dans Nom Unicode du fichier à hacher.  
  
 `piHashAlg`  
 [in, out] Algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par l’CryptoAPI Win32. Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 à Tableau d’octets contenant le hachage généré.  
  
 `cchHash`  
 dans Taille maximale de la mémoire tampon vers laquelle pointe `pbHash` .  
  
 `pchHash`  
 à Taille, en octets, de `pbHash` .  
  
## <a name="remarks"></a>Remarques  

 Cette fonction est identique à [GetHashFromFile (](gethashfromfile-function.md), à ceci près que la spécification de nom de fichier est au format Unicode au lieu de ANSI.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFileW, méthode](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, méthode](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
