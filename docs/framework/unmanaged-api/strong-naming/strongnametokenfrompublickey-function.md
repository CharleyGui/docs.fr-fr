---
title: StrongNameTokenFromPublicKey, fonction
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175055"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey, fonction
Obtient un jeton représentant une clé publique. Un jeton de nom fort est la forme raccourcie d’une clé publique.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKeyBlob`  
 [dans] Une structure de type [PublicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.  
  
 `cbPublicKeyBlob`  
 [dans] La taille, dans les `pbPublicKeyBlob`octets, de .  
  
 `ppbStrongNameToken`  
 [out] Le jeton de nom fort `pbPublicKeyBlob`correspondant à la clé passée dedans . Le runtime de langue commune alloue la mémoire dans laquelle retourner le jeton. L’appelant doit libérer cette mémoire en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbStrongNameToken`  
 [out] La taille, dans les octets, du jeton de nom fort retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`à la réussite; autrement, `false`.  
  
## <a name="remarks"></a>Notes   
 Un jeton de nom fort est la forme raccourcie d’une clé publique utilisée pour économiser de l’espace lors du stockage des informations clés dans les métadonnées. Plus précisément, des jetons de nom forts sont utilisés dans les références d’assemblage pour désigner l’assemblage dépendant.  
  
 Si `StrongNameTokenFromPublicKey` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans mscoree.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameTokenFromPublicKey, méthode](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey, méthode](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob, structure](publickeyblob-structure.md)
