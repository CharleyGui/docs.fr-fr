---
title: StrongNameSignatureSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176888"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize, fonction
Retourne la taille de la signature de nom fort. `StrongNameSignatureSize`est généralement utilisé par les compilateurs pour déterminer combien d’espace réserver dans le fichier lors de la création d’un assemblage signé retard.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKeyBlob`  
 [dans] Une structure de type [PublicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.  
  
 `cbPublicKeyBlob`  
 [dans] La taille, dans les `pbPublicKeyBlob`octets, de .  
  
 `pcbSize`  
 [dans] Le nombre d’octets requis pour stocker la signature du nom fort.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`à la réussite; autrement, `false`.  
  
## <a name="remarks"></a>Notes   
 Si `StrongNameSignatureSize` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureSize, méthode](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
