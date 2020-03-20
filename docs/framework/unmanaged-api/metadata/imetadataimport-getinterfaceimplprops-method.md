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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175380"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps, méthode
Obtient un pointeur pour les jetons <xref:System.Type> de métadonnées pour le qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.
  
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
 [dans] Le jeton des métadonnées représentant la méthode pour retourner les jetons de classe et d’interface pour.  
  
 `pClass`  
 [out] Le jeton des métadonnées représentant la classe qui met en œuvre la méthode.  
  
 `ptkIface`  
 [out] Le jeton des métadonnées représentant l’interface qui définit la méthode mise en œuvre.  

## <a name="remarks"></a>Notes 

 Vous obtenez la `iImpl` valeur pour appeler la méthode [EnumInterfaceImpls.](imetadataimport-enuminterfaceimpls-method.md)

 Supposons, par exemple, `mdTypeDef` qu’une classe a une valeur symbolique de 0x02000007 et qu’elle implémente trois interfaces dont les types ont des jetons :

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Conceptuellement, ces informations sont stockées dans une table de mise en œuvre d’interface comme :

| Numéro de rangée | Jeton de classe | Jeton d’interface |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Rappelons que le jeton est une valeur de 4 byte :

- Les 3 octets inférieurs détiennent le numéro de rangée, ou RID.
- Le haut byte détient le type symbolique - `mdtInterfaceImpl`0x09 pour .

`GetInterfaceImplProps`retourne l’information détenue dans la rangée `iImpl` dont vous fournissez le jeton dans l’argument.
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
