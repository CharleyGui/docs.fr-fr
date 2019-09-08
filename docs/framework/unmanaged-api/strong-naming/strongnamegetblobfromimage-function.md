---
title: StrongNameGetBlobFromImage, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799084"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage, fonction
Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameGetBlobFromImage (](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbBase`  
 dans Adresse mémoire du manifeste de l’assembly mappé.  
  
 `dwLength`  
 dans Taille, en octets, de l’image à `pbBase`.  
  
 `pbBlob`  
 dans Mémoire tampon destinée à contenir la représentation binaire de l’image.  
  
 `pcbBlob`  
 [in, out] Taille maximale demandée, en octets, de `pbBlob`. Lors du retour, taille réelle, en octets, de `pbBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si la `StrongNameGetBlobFromImage` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetBlobFromImage, méthode](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob, méthode](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
