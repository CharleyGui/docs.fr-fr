---
title: StrongNameTokenFromAssemblyEx, fonction
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 566bba09f6bfac2f7616dc5caf32ef431f2e1e67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719799"
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx, fonction

Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique que le jeton représente.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameTokenFromAssemblyEx (](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszFilePath`  
 dans Chemin d’accès au fichier exécutable portable (PE) pour l’assembly.  
  
 `ppbStrongNameToken`  
 à Jeton de nom fort retourné.  
  
 `pcbStrongNameToken`  
 à Taille, en octets, du jeton de nom fort.  
  
 `ppbPublicKeyBlob`  
 à Clé publique retournée.  
  
 `pcbPublicKeyBlob`  
 à Taille, en octets, de la clé publique.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` en cas de réussite de l’opération ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Un jeton de nom fort est la forme raccourcie d’une clé publique. Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly. Le jeton fait partie du nom fort de l’assembly et peut être lu à partir des métadonnées de l’assembly.  
  
 Une fois la clé récupérée et le jeton créé, vous devez appeler la fonction [StrongNameFreeBuffer](strongnamefreebuffer-function.md) pour libérer la mémoire allouée.  
  
 Si la `StrongNameTokenFromAssemblyEx` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans mscoree.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromAssembly, méthode](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly, méthode](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
