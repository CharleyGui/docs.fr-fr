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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176979"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile, fonction
Génère un hachage sur le contenu du fichier spécifié.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::GetHashDeFile](../hosting/iclrstrongname-gethashfromfile-method.md) méthode à la place.  
  
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
 [dans] Le nom du fichier au hachage.  
  
 `piHashAlg`  
 [dans, dehors] L’algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par le CryptoAPI Win32. Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 [out] Un tableau d’en-lieu contenant le hachage généré.  
  
 `cchHash`  
 [dans] La taille maximale du `pbHash` tampon qui indique.  
  
 `pchHash`  
 [out] La taille, dans les octets, du retour `pbHash`.  
  
## <a name="remarks"></a>Notes   
 Cette fonction est la même que [GetHashFromFileW](gethashfromfilew-function.md), sauf que la spécification nom de fichier est ANSI au lieu d’Unicode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromFile, méthode](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW, méthode](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
