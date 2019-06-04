---
title: CreateICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57163ccfcc6dff343a8bbc7d63564ae6b57b5ff6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490501"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen, fonction
Crée un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ceeFileGen`  
 [out] Un pointeur vers l’adresse d’un nouveau `ICeeFileGen` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard.  
  
## <a name="remarks"></a>Notes  
 Le `ICeeFileGen` objet est utilisé pour créer de common language runtime (CLR) les fichiers exécutables portables (PE).  
  
 Appelez le [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) fonction détruire le `ICeeFileGen` issue de l’objet.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ICeeFileGen.h  
  
 **Bibliothèque :** MSCorPE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
