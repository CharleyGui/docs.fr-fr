---
title: IMetaDataEmit::GetSaveSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777393"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize, méthode
Obtient la taille binaire estimée de l’assembly et ses métadonnées dans la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fSave`  
 [in] Une valeur de la [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) énumération qui spécifie s’il faut obtenir une taille exacte ou approximative. Seuls les trois valeurs sont valides : cssAccurate, cssQuick et cssDiscardTransientCAs :  
  
- cssAccurate retourne la taille d’enregistrement exact, mais prend plus de temps à calculer.  
  
- cssQuick retourne une taille, remplie pour la sécurité, mais prend moins de temps à calculer.  
  
- cssDiscardTransientCAs indique à `GetSaveSize` qu’il peut jeter des attributs personnalisés pouvant être éliminées.  
  
 `pdwSaveSize`  
 [out] Un pointeur vers la taille qui est requis pour enregistrer le fichier.  
  
## <a name="remarks"></a>Notes  
 `GetSaveSize` calcule l’espace requis, en octets, pour enregistrer l’assembly et toutes ses métadonnées dans la portée actuelle. (Un appel à la [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) méthode émet ce nombre d’octets.)  
  
 Si l’appelant implémente le [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (via [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` effectue deux passes sur les métadonnées pour optimiser et les compresser. Sinon, aucune des optimisations.  
  
 Si l’optimisation est effectuée, le premier passage trie simplement les structures de métadonnées pour régler les performances des recherches au moment de l’importation. Cette étape se produit généralement dans le déplacement des enregistrements, avec comme conséquence que les jetons conservés par l’outil pour référence ultérieure sont invalidés. Les métadonnées ne pas informent l’appelant de ces modifications apportées aux jetons jusqu’après la deuxième passe, toutefois. Dans la deuxième passe, différents des optimisations qui sont destinées à réduire la taille globale des métadonnées, telles que l’optimisation (liaison anticipée) `mdTypeRef` et `mdMemberRef` jetons lors de la référence concerne un type ou membre qui est déclaré dans le portée des métadonnées actuelle. Dans cette étape, une autre série de mappages de jetons se produit. Après ce passage, le moteur de métadonnées informe l’appelant, via son `IMapToken` interface, de n’importe quel modifié les valeurs de jeton.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
