---
title: IMetaDataImport::GetInterfaceImplProps, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437538"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps, méthode
Obtient un pointeur vers les jetons de métadonnées pour le <xref:System.Type> qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iiImpl`  
 dans Jeton de métadonnées représentant la méthode pour laquelle retourner la classe et les jetons d’interface.  
  
 `pClass`  
 à Jeton de métadonnées représentant la classe qui implémente la méthode.  
  
 `ptkIface`  
 à Jeton de métadonnées représentant l’interface qui définit la méthode implémentée.  

## <a name="remarks"></a>Notes

 Vous obtenez la valeur de `iImpl` en appelant la méthode [EnumInterfaceImpls,](imetadataimport-enuminterfaceimpls-method.md) .
 
 Par exemple, supposons qu’une classe ait une `mdTypeDef` valeur de jeton de 0x02000007 et qu’elle implémente trois interfaces dont les types ont des jetons : 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Conceptuellement, ces informations sont stockées dans une table d’implémentation d’interface comme suit :

| Numéro de ligne | Jeton de classe | Jeton d’interface |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Rappelez-vous que le jeton est une valeur de 4 octets :

- Les 3 octets inférieurs contiennent le numéro de ligne, ou RID.
- L’octet supérieur contient le type de jeton – 0x09 pour `mdtInterfaceImpl`.

`GetInterfaceImplProps` retourne les informations contenues dans la ligne dont vous indiquez le jeton dans l’argument `iImpl`. 
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
