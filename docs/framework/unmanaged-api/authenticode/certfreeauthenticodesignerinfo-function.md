---
title: CertFreeAuthenticodeSignerInfo, fonction
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674175"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo, fonction

Libère les ressources allouées pour la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pSignerInfo`  
 [en entrée, en sortie] Les informations du signataire à libérer. Consultez la structure [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` si la fonction réussit. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
