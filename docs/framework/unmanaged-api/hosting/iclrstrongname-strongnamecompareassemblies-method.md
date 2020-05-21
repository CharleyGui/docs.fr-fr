---
title: Méthode ICLRStrongName::StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: 0087636c68d0748ad2b143de9b132278ab9d43f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762056"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>Méthode ICLRStrongName::StrongNameCompareAssemblies
Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszAssembly1`  
 dans Chemin d’accès au premier assembly.  
  
 `wszAssembly2`  
 dans Chemin d’accès au deuxième assembly.  
  
 `pdwResult`  
 à L’une des valeurs suivantes :  
  
- `SN_CMP_DIFFERENT`(0) : spécifie que les assemblys contiennent des données différentes.  
  
- `SN_CMP_IDENTICAL`(1) : spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et leur somme de contrôle.  
  
- `SN_CMP_SIGONLY`(2) : spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Notes  
 La signature de nom fort d’un assembly se compose du nom de texte, de la version, de la culture et du jeton de clé publique de l’assembly.  
  
## <a name="see-also"></a>Voir aussi

- [ICLRStrongName, interface](iclrstrongname-interface.md)
