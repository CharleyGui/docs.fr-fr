---
title: Méthode ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 46345ae570673c9c9c0c58fb6edea1464ba8dd91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671692"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a>Méthode ICLRStrongName::StrongNameKeyDelete

Supprime le conteneur de clé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszKeyContainer`  
 dans Nom du conteneur de clé à supprimer.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).  
  
## <a name="remarks"></a>Remarques  

 Utilisez la méthode [ICLRStrongName :: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) pour importer une paire de clés publique/privée dans un conteneur.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameKeyInstall, méthode](iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName, interface](iclrstrongname-interface.md)
