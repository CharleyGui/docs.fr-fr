---
title: GetHashFromFile, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ffa25b1ec6fda80099f333c1d0a4cf57b76379e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140688"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile, fonction
Génère un hachage sur le contenu du fichier spécifié.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: GetHashFromFile (](../hosting/iclrstrongname-gethashfromfile-method.md) à la place.  
  
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
 dans Taille maximale de la mémoire tampon vers laquelle `pbHash` pointe.  
  
 `pchHash`  
 à Taille, en octets, de la `pbHash`retournée.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est identique à [GetHashFromFileW (](gethashfromfilew-function.md), à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFile, méthode](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW, méthode](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
