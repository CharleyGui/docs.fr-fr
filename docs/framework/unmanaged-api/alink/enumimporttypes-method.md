---
title: EnumImportTypes, méthode
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448738"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes, méthode

Énumère chaque type dans chaque portée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Paramètres

`hEnum`\
Handle pour l’énumérateur.

`dwMax`\
Nombre maximal de types à récupérer.

`aTypeDefs`\
Reçoit des jetons de type, sans dépasser `dwMax`.

`pdwCount`\
Reçoit le nombre réel de types dans `aTypeDefs`.

## <a name="return-value"></a>Valeur de retour

Retourne S_OK si la méthode est réussie.

## <a name="requirements"></a>Configuration requise

Requiert ALink. h

## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
