---
title: Fonctions externes
description: En savoir plus F# sur la prise en charge linguistique pour l’appel de fonctions en code natif.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968735"
---
# <a name="external-functions"></a>Fonctions externes

Cette rubrique décrit F# la prise en charge linguistique pour l’appel de fonctions en code natif.

## <a name="syntax"></a>Syntaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, les *arguments* représentent les arguments fournis à l' `System.Runtime.InteropServices.DllImportAttribute` attribut. Le premier argument est une chaîne qui représente le nom de la DLL qui contient cette fonction, sans l’extension. dll. Des arguments supplémentaires peuvent être fournis pour toutes les propriétés publiques de la `System.Runtime.InteropServices.DllImportAttribute` classe, telles que la Convention d’appel.

Supposons que vous avez C++ une DLL native qui contient la fonction exportée suivante.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Vous pouvez appeler cette fonction à F# partir de à l’aide du code suivant.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

L’interopérabilité avec le code natif est appelée *appel* de code non managé et est une fonctionnalité du CLR. Pour plus d’informations, consultez [Interopération avec du code non managé](../../../framework/interop/index.md). Les informations contenues dans cette section s' F#appliquent à.

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
