---
title: Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379319"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo

Récupère un mappage de dictionnaire générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Paramètres

`ppMemoryBuffer`\
à Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) contenant le mappage de dictionnaire générique. Pour plus d'informations, consultez la section Remarques.

## <a name="remarks"></a>Remarks

> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.

Le mappage se compose de deux sections de niveau supérieur :

- [Répertoire](#Directory) contenant les adresses virtuelles relatives (RVA) de tous les dictionnaires inclus dans ce mappage.

- [Segment](#Heap) aligné sur les octets qui contient les informations d’instanciation de l’objet. Il commence immédiatement après la dernière entrée du répertoire.

<a name="Directory"></a>

## <a name="the-directory"></a>Répertoire

Chaque entrée du répertoire fait référence à un offset dans le tas, c'est-à-dire un offset par rapport au début du tas. La valeur d'entrées individuelles n'est pas nécessairement unique : il est possible que plusieurs entrées de répertoire pointent vers le même offset dans le tas.

La structure de la partie répertoire du mappage de dictionnaire générique est la suivante :

- Les 4 premiers octets contiennent le nombre d'entrées de dictionnaire (c'est-à-dire le nombre d'adresses virtuelles relatives dans le dictionnaire). Nous faisons référence à cette valeur en tant que *N*. Si le bit élevé est défini, les entrées sont triées par adresse virtuelle relative dans l’ordre croissant.

- Les *entrées* d’annuaire sont les suivantes. Chaque entrée se compose de 8 octets dans deux segments de 4 octets :

  - Octets 0-3 : adresse RVA (adresse virtuelle relative du dictionnaire)

  - Octets 4-7 : offset (offset par rapport au début du tas)

<a name="Heap"></a>

## <a name="the-heap"></a>Tas

La taille du tas peut être calculée par un lecteur de flux en soustrayant la longueur du flux de la taille du répertoire + 4. En d’autres termes :

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

où la taille du répertoire est `N * 8`.

Le format de chaque élément d'informations d'instanciation sur le tas est le suivant :

- La longueur de cet élément d'informations d'instanciation en octets au format de métadonnées ECMA compressé. La valeur exclut ces informations de longueur.

- Nombre de types d’instanciation générique, ou *T*, au format de métadonnées ECMA compressé.

- Types *T* , chacun représenté dans le format de signature de type ECMA.

L'inclusion de la longueur de chaque élément de tas permet d'effectuer un tri simple de la section répertoire sans affecter le tas.

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider2, interface](icordebugsymbolprovider2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
