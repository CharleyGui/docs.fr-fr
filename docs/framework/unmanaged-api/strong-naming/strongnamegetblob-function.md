---
title: StrongNameGetBlob, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799100"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob, fonction
Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameGetBlob (](../hosting/iclrstrongname-strongnamegetblob-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 dans Chemin d’accès valide au fichier exécutable à charger.  
  
 `pbBlob`  
 dans Mémoire tampon dans laquelle charger le fichier exécutable.  
  
 `pcbBlob`  
 [in, out] Taille maximale demandée, en octets, de `pbBlob`. Lors du retour, taille réelle, en octets, de `pbBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si la `StrongNameGetBlob` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetBlob, méthode](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage, méthode](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
