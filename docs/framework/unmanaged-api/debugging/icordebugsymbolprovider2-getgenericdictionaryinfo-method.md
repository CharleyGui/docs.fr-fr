---
title: 'Icordebugsymbolprovider2, :: GetGenericDictionaryInfo, méthode'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: c9f7206cac54d64c28eb50d81fea00a6f3c494d4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133633"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Icordebugsymbolprovider2, :: GetGenericDictionaryInfo, méthode

Récupère un mappage de dictionnaire générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Paramètres

`ppMemoryBuffer`\
à Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) contenant le mappage de dictionnaire générique. Pour plus d'informations, consultez la section Notes.

## <a name="remarks"></a>Notes

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

La taille du tas peut être calculée par un lecteur de flux en soustrayant la longueur du flux de la taille du répertoire + 4. En d'autres termes :

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

où la taille du répertoire est `N * 8`.

Le format de chaque élément d'informations d'instanciation sur le tas est le suivant :

- La longueur de cet élément d'informations d'instanciation en octets au format de métadonnées ECMA compressé. La valeur exclut ces informations de longueur.

- Nombre de types d’instanciation générique, ou *T*, au format de métadonnées ECMA compressé.

- Types *T* , chacun représenté dans le format de signature de type ECMA.

L'inclusion de la longueur de chaque élément de tas permet d'effectuer un tri simple de la section répertoire sans affecter le tas.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorDebug.idl, CorDebug.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorDebugSymbolProvider2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
