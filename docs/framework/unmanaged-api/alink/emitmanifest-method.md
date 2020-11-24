---
title: EmitManifest, méthode
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: b1c005e58f18b03a7da5f3836f719b95c41bca95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684939"
---
# <a name="emitmanifest-method"></a>EmitManifest, méthode

Émet le manifeste final. Appelez cette méthode après l’importation de tous les autres fichiers et la définition de toutes les options. N’appelez pas cette méthode pour les modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly.  
  
 `pdwReserveSize`  
 Reçoit la taille à réserver dans le fichier d’assembly, récupérée à partir de la [fonction StrongNameSignatureSize (](../strong-naming/strongnamesignaturesize-function.md).  
  
 `ptkManifest`  
 Reçoit éventuellement le jeton du manifeste de l’assembly.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
