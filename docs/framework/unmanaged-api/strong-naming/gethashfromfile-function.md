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
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732370"
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
 dans Taille maximale de la mémoire tampon `pbHash` vers laquelle pointe.  
  
 `pchHash`  
 à Taille, en octets, du retourné `pbHash` .  
  
## <a name="remarks"></a>Remarques  

 Cette fonction est identique à [GetHashFromFileW (](gethashfromfilew-function.md), à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFile, méthode](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW, méthode](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
