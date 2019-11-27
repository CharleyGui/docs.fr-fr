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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434333"
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize, méthode
Obtient la taille estimée en binaire de l’assembly et de ses métadonnées dans la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fSave`  
 dans Valeur de l’énumération [CorSaveSize,](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) qui spécifie s’il faut obtenir une taille exacte ou approximative. Seules trois valeurs sont valides : cssAccurate, cssQuick et cssDiscardTransientCAs :  
  
- cssAccurate retourne la taille d’enregistrement exacte, mais met plus de temps à calculer.  
  
- cssQuick retourne une taille, complétée pour des raisons de sécurité, mais prend moins de temps pour le calcul.  
  
- cssDiscardTransientCAs indique `GetSaveSize` qu’il peut lever des attributs personnalisés pouvant être éliminés.  
  
 `pdwSaveSize`  
 à Pointeur vers la taille requise pour enregistrer le fichier.  
  
## <a name="remarks"></a>Notes  
 `GetSaveSize` calcule l’espace nécessaire, en octets, pour enregistrer l’assembly et toutes ses métadonnées dans l’étendue actuelle. (Un appel à la méthode [IMetaDataEmit :: SaveToStream,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) émettra ce nombre d’octets.)  
  
 Si l’appelant implémente l’interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (via [IMetaDataEmit :: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit :: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` effectue deux passes sur les métadonnées pour les optimiser et les compresser. Dans le cas contraire, aucune optimisation n’est effectuée.  
  
 Si l’optimisation est effectuée, la première passe trie simplement les structures de métadonnées pour régler les performances des recherches au moment de l’importation. En général, cette étape entraîne le déplacement des enregistrements, avec l’effet secondaire que les jetons conservés par l’outil pour référence ultérieure sont invalidés. Toutefois, les métadonnées n’informent pas l’appelant de ces modifications de jeton jusqu’à la deuxième passe. Au cours de la deuxième passe, différentes optimisations sont effectuées pour réduire la taille globale des métadonnées, telles que l’optimisation de la `mdTypeRef` et des jetons de `mdMemberRef` lorsque la référence est un type ou un membre déclaré dans la portée des métadonnées actuelle. Dans cette étape, un autre mappage de jetons est effectué. Après cette étape, le moteur de métadonnées avertit l’appelant, via son interface `IMapToken`, des valeurs de jeton modifiées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
