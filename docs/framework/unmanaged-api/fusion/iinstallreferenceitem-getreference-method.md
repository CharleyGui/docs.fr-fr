---
title: IInstallReferenceItem::GetReference, méthode
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 14286970a4f7093d72b47b780ea880f5ccb1bca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721073"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference, méthode

Obtient un pointeur vers la structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) représentée par cet objet [IInstallReferenceItem](iinstallreferenceitem-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppRefData`  
 à Pointeur retourné `FUSION_INSTALL_REFERENCE` .  
  
 `dwFlags`  
 dans Réservé pour une future extensibilité. `dwFlags` doit avoir la valeur 0 (zéro).  
  
 `pvReserved`  
 dans Réservé pour une future extensibilité. `pvReserved` doit être une référence null.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IInstallReferenceItem, interface](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE, structure](fusion-install-reference-structure.md)
