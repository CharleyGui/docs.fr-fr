---
title: ExportTypeForwarder, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 36c99477e9faead5e24799d5b0ae8901f1dd13c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448708"
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder, méthode
Ajoute un redirecteur de type à la table de types de l’assembly donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `tkAssemblyRef`  
 Référence à l’assembly auquel le redirecteur de type fait référence.  
  
 `pszTypename`  
 Nom de type qualifié complet à exporter.  
  
 `dwFlags`  
 `ComType` indicateurs tels que `tdPublic` ou `tdNested`. Cette valeur peut être passée à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Reçoit le jeton du type exporté. Cela est nécessaire uniquement pour l’émission de types imbriqués.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
