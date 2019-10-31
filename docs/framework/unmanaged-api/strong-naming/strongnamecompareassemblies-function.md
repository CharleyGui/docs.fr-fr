---
title: StrongNameCompareAssemblies, fonction
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140622"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies, fonction
Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameCompareAssemblies (](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
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
  
- `SN_CMP_DIFFERENT` (0) : spécifie que les assemblys contiennent des données différentes.  
  
- `SN_CMP_IDENTICAL` (1) : spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et leur somme de contrôle.  
  
- `SN_CMP_SIGONLY` (2) : spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Notes  
 La signature de nom fort d’un assembly se compose du nom de texte, de la version, de la culture et du jeton de clé publique de l’assembly.  
  
 Si la fonction `StrongNameCompareAssemblies` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameCompareAssemblies, méthode](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
