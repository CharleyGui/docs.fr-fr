---
title: IMetaDataTables::GetNextUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c50740e59019edb44f6e8c2cee1b823fa047a039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781438"
---
# <a name="imetadatatablesgetnextuserstring-method"></a>IMetaDataTables::GetNextUserString, méthode
Obtient l’index de la ligne qui contient la chaîne codée en dur suivante dans la colonne de table actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixUserString`  
 [in] Une valeur d’index à partir de la colonne de chaîne actuelle.  
  
 `pNext`  
 [out] Pointeur vers l’index de ligne de la chaîne suivante dans la colonne.  
  
## <a name="remarks"></a>Notes  
 Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents. Pour plus d’informations sur le tableau GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : Metadata Definition and Semantics ». La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
