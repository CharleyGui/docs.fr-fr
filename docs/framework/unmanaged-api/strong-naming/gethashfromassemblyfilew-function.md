---
title: GetHashFromAssemblyFileW, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140702"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW, fonction
Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié. Le chemin d’accès au fichier d’assembly doit être spécifié sous la forme d’une chaîne Unicode.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: GetHashFromAssemblyFileW (](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 dans Chemin d’accès au fichier à hacher. Ce paramètre doit être une chaîne Unicode.  
  
 `piHashAlg`  
 [in, out] Constante qui spécifie l’algorithme de hachage. Utilisez zéro pour l’algorithme de hachage par défaut.  
  
 `pbHash`  
 à Mémoire tampon de hachage retournée.  
  
 `cchHash`  
 dans Taille maximale de `pbHash`demandée.  
  
 `pchHash`  
 à Taille retournée, en octets, de `pbHash`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetHashFromAssemblyFileW, méthode](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile, méthode](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
