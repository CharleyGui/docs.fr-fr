---
title: EmitAssemblyCustomAttribute, méthode
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: 2070d1ec2aec80638c20c764eed5086c4a42e0fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676359"
---
# <a name="emitassemblycustomattribute-method"></a>EmitAssemblyCustomAttribute, méthode

Appelez pour définir des attributs personnalisés au niveau de l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 Fichier qui défile l’attribut. Peut avoir la valeur NULL si `AssemblyID` n’indique pas un netmodule indépendant.  
  
 `tkType`  
 Type de l’attribut personnalisé.  
  
 `pCustomValue`  
 Données de valeur personnalisée.  
  
 `cbCustomValue`  
 Longueur des données de la valeur personnalisée.  
  
 `bSecurity`  
 TRUE si l’attribut personnalisé est lié à la signature de l’assembly.  
  
 `bAllowMulti`  
 TRUE si plusieurs attributs doivent être émis.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
