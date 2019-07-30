---
title: Identificateurs de ligne, de fichier et de chemin d’accès source
description: Découvrez comment utiliser des valeurs d' F# identificateur intégrées qui vous permettent d’accéder au numéro de ligne source, au répertoire et au nom de fichier dans votre code.
ms.date: 05/16/2016
ms.openlocfilehash: 5ff36210edc75370f8baf9ee7be057f3ac0c3979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627116"
---
# <a name="source-line-file-and-path-identifiers"></a>Identificateurs de ligne, de fichier et de chemin d’accès source

Les identificateurs `__LINE__`, `__SOURCE_DIRECTORY__` et `__SOURCE_FILE__` sont des valeurs intégrées qui vous permettent d’accéder au numéro de ligne source, au répertoire et au nom de fichier dans votre code.

## <a name="syntax"></a>Syntaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Notes

Chacune de ces valeurs est de `string`type.

Le tableau suivant récapitule les identificateurs de ligne, de fichier et de chemin d’accès source qui F#sont disponibles dans. Ces identificateurs ne sont pas des macros de préprocesseur; Il s’agit de valeurs intégrées qui sont reconnues par le compilateur.

|Identificateur prédéfini|Description|
|---------------------|-----------|
|`__LINE__`|Prend la valeur du numéro de ligne en cours `#line` , en considérant les directives.|
|`__SOURCE_DIRECTORY__`|Prend la valeur du chemin d’accès complet actuel du répertoire source, `#line` en prenant en compte les directives.|
|`__SOURCE_FILE__`|Prend le nom du fichier source actuel, sans son chemin d’accès, `#line` en prenant en compte les directives.|

Pour plus d’informations sur `#line` la directive, consultez [directives de compilateur](compiler-directives.md).

## <a name="example"></a>Exemple

L’exemple de code suivant illustre l’utilisation de ces valeurs.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Sortie :

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Voir aussi

- [Directives de compilateur](compiler-directives.md)
- [Informations de référence du langage F#](index.md)
