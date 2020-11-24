---
title: SetPEKind, méthode
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: be8a11cbf70e2c6f19ace67648b124515c1fb3c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680038"
---
# <a name="setpekind-method"></a>SetPEKind, méthode

Détermine le type d’exécutable portable, propre à l’ordinateur ou indépendant de l’ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 Jeton du fichier pour lequel le type PE doit être défini. Peut avoir la valeur NULL si `AssemblyID` n’indique pas un netmodule indépendant.  
  
 `dwPEKind`  
 Type de PE, comme indiqué par l' [énumération CorPEKind,](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 Architecture de l’ordinateur cible, comme indiqué dans l’en-tête NT.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [GetPEKind, méthode](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
