---
title: ISOSDacInterface, interface
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420966"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface, interface

Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS` .

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Méthodes

| Méthode                                                                                                               | Description                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | Obtient les données pour le pointeur MethodDesc donné. |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée. |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| Récupère les données correspondant au module chargé à une adresse donnée. |

## <a name="remarks"></a>Notes

Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque. Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `436f00f2-b42a-4b9f-870c-e73db66ae930` un GUID qui peut être obtenu par le biais des mécanismes com habituels.

## <a name="requirements"></a>Conditions requises

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
**En-tête :** None  
**Bibliothèque :** None  
**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Voir aussi

- [Débogage](index.md)
- [Interfaces de débogage](debugging-interfaces.md)
