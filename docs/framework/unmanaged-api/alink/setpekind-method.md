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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179391"
---
# <a name="setpekind-method"></a>SetPEKind, méthode
Détermine le type portable exécutable, spécifique à la machine ou agnostique à la machine.  
  
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
 ID de l’assemblage.  
  
 `FileToken`  
 Jeton de fichier pour lequel le type PE doit être défini. Peut être `AssemblyID` NULL si n’indique pas un netmodule non lié.  
  
 `dwPEKind`  
 Le type de PE, comme indiqué par le [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).  
  
 `dwMachine`  
 L’architecture de la machine cible, comme indiqué dans l’en-tête NT.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Spécifications  
 Nécessite alink.h.  
  
## <a name="see-also"></a>Voir aussi

- [GetPEKind, méthode](../metadata/imetadataimport2-getpekind-method.md)
- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
