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
ms.openlocfilehash: feb81b86190f953b50f43f244f4e58a0a482f86e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003917"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd, méthode

Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels antérieurs à [IMetaDataEmit :: Merge](imetadataemit-merge-method.md).

## <a name="syntax"></a>Syntaxe

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Paramètres

Cette méthode n’accepte aucun paramètre.

## <a name="remarks"></a>Remarques

Cette routine déclenche la fusion réelle des métadonnées, de toutes les étendues d’importation spécifiées par les appels précédents à `IMetaDataEmit::Merge` , dans l’étendue de sortie actuelle.

Les conditions spéciales suivantes s’appliquent à la fusion :

- Un identificateur de version de module (MVID) n’est jamais importé, car il est unique aux métadonnées dans la portée d’importation.

- Aucune propriété existante à l’ensemble du module n’est remplacée.

  Si des propriétés de module ont déjà été définies pour l’étendue actuelle, aucune propriété de module n’est importée. Toutefois, si les propriétés du module n’ont pas été définies dans la portée actuelle, elles ne sont importées qu’une seule fois, quand elles sont rencontrées pour la première fois. Si ces propriétés de module sont à nouveau rencontrées, il s’agit de doublons. Si les valeurs de toutes les propriétés de module (à l’exception de MVID) sont comparées et qu’aucun doublon n’est trouvé, une erreur est générée.

- Pour les définitions de type ( `TypeDef` ), aucun doublon n’est fusionné dans l’étendue actuelle. `TypeDef`les objets sont vérifiés pour les doublons par rapport à chaque numéro *de*  +  *GUID*  +  *version*GUID du nom d’objet complet. S’il existe une correspondance sur un nom ou un GUID et que l’un des deux autres éléments est différent, une erreur est générée. Sinon, si les trois éléments correspondent, `MergeEnd` effectue un contrôle de curseur pour s’assurer que les entrées sont effectivement des doublons ; dans le cas contraire, une erreur est générée. Ce contrôle de curseur recherche les éléments suivants :

  - Les mêmes déclarations de membre, qui se produisent dans le même ordre. Les membres marqués comme `mdPrivateScope` (Voir l’énumération [CorMethodAttr,](cormethodattr-enumeration.md) ) ne sont pas inclus dans cette vérification ; ils sont fusionnés de manière spéciale.

  - La même disposition de classe.

  Cela signifie qu’un `TypeDef` objet doit toujours être défini de manière complète et cohérente dans chaque étendue de métadonnées dans laquelle il est déclaré ; si ses implémentations de membre (pour une classe) sont réparties sur plusieurs unités de compilation, la définition complète est supposée être présente dans chaque portée et non incrémentielle pour chaque étendue. Par exemple, si les noms de paramètres sont pertinents pour le contrat, ils doivent être émis de la même manière dans toutes les étendues ; Si elles ne sont pas pertinentes, elles ne doivent pas être émises dans les métadonnées.

  L’exception est qu’un `TypeDef` objet peut avoir des membres incrémentiels marqués comme `mdPrivateScope` . Si vous les rencontrez, les `MergeEnd` ajoute de manière incrémentielle à la portée actuelle sans tenir compte des doublons. Étant donné que le compilateur comprend la portée privée, le compilateur doit être responsable de l’application des règles.

- Les adresses virtuelles relatives (RVA) ne sont pas importées ou fusionnées ; le compilateur est supposé émettre à nouveau ces informations.

- Les attributs personnalisés sont fusionnés uniquement lorsque l’élément auquel ils sont attachés est fusionné. Par exemple, les attributs personnalisés associés à une classe sont fusionnés lorsque la classe est rencontrée pour la première fois. Si des attributs personnalisés sont associés à un `TypeDef` ou `MemberDef` qui est spécifique à l’unité de compilation (telle que l’horodatage d’une compilation de membre), ils ne sont pas fusionnés et il revient au compilateur de supprimer ou de mettre à jour ces métadonnées.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Cor. h

**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll

**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
