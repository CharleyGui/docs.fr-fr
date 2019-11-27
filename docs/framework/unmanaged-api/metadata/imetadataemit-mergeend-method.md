---
title: IMetaDataEmit::MergeEnd, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448029"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd, méthode

Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels antérieurs à [IMetaDataEmit :: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>Syntaxe

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Paramètres

Cette méthode n’accepte aucun paramètre.

## <a name="remarks"></a>Notes

Cette routine déclenche la fusion réelle des métadonnées, de toutes les étendues d’importation spécifiées par les appels précédents à `IMetaDataEmit::Merge`, dans l’étendue de sortie actuelle.

Les conditions spéciales suivantes s’appliquent à la fusion :

- Un identificateur de version de module (MVID) n’est jamais importé, car il est unique aux métadonnées dans la portée d’importation.

- Aucune propriété existante à l’ensemble du module n’est remplacée.

  Si des propriétés de module ont déjà été définies pour l’étendue actuelle, aucune propriété de module n’est importée. Toutefois, si les propriétés du module n’ont pas été définies dans la portée actuelle, elles ne sont importées qu’une seule fois, quand elles sont rencontrées pour la première fois. Si ces propriétés de module sont à nouveau rencontrées, il s’agit de doublons. Si les valeurs de toutes les propriétés de module (à l’exception de MVID) sont comparées et qu’aucun doublon n’est trouvé, une erreur est générée.

- Pour les définitions de type (`TypeDef`), aucun doublon n’est fusionné dans l’étendue actuelle. les objets `TypeDef` sont recherchés en tant que doublons pour chaque *nom d’objet* complet + le *numéro de version*du *GUID* + . S’il existe une correspondance sur un nom ou un GUID et que l’un des deux autres éléments est différent, une erreur est générée. Sinon, si les trois éléments correspondent, `MergeEnd` effectue un contrôle de curseur pour s’assurer que les entrées sont effectivement des doublons ; Si ce n’est pas le cas, une erreur est générée. Ce contrôle de curseur recherche les éléments suivants :

  - Les mêmes déclarations de membre, qui se produisent dans le même ordre. Les membres marqués comme `mdPrivateScope` (Voir l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) ) ne sont pas inclus dans cette vérification ; elles sont fusionnées de manière spéciale.

  - La même disposition de classe.

  Cela signifie qu’un objet `TypeDef` doit toujours être défini de manière complète et cohérente dans chaque portée de métadonnées dans laquelle il est déclaré ; Si ses implémentations de membres (pour une classe) sont réparties sur plusieurs unités de compilation, la définition complète est supposée être présente dans chaque portée et non incrémentielle pour chaque étendue. Par exemple, si les noms de paramètres sont pertinents pour le contrat, ils doivent être émis de la même manière dans toutes les étendues ; Si elles ne sont pas pertinentes, elles ne doivent pas être émises dans les métadonnées.

  L’exception est qu’un objet `TypeDef` peut avoir des membres incrémentiels marqués comme `mdPrivateScope`. Si vous les rencontrez, `MergeEnd` les ajoute de manière incrémentielle à la portée actuelle sans tenir compte des doublons. Étant donné que le compilateur comprend la portée privée, le compilateur doit être responsable de l’application des règles.

- Les adresses virtuelles relatives (RVA) ne sont pas importées ou fusionnées ; le compilateur est supposé émettre à nouveau ces informations.

- Les attributs personnalisés sont fusionnés uniquement lorsque l’élément auquel ils sont attachés est fusionné. Par exemple, les attributs personnalisés associés à une classe sont fusionnés lorsque la classe est rencontrée pour la première fois. Si des attributs personnalisés sont associés à un `TypeDef` ou `MemberDef` qui est spécifique à l’unité de compilation (telle que l’horodatage d’une compilation de membre), ils ne sont pas fusionnés et il revient au compilateur de supprimer ou de mettre à jour ces métadonnées.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** Cor. h

**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll

**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
