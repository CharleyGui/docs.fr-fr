---
title: P/Invoke inter-plateformes
description: Découvrez les chemins que le runtime doit rechercher lors du chargement des bibliothèques natives via P/Invoke. Découvrez également comment utiliser SetDllImportResolver.
author: saul
ms.date: 01/31/2021
ms.openlocfilehash: 40ad87fe537ad043a488e4086814a58ef8e0211e
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427484"
---
# <a name="writing-cross-platform-pinvoke-code"></a>Écriture de code P/Invoke multiplateforme

## <a name="library-name-variations"></a>Variantes de nom de bibliothèque

Pour faciliter le code P/Invoke Cross-Platform plus simple, le runtime ajoute l’extension de bibliothèque partagée canonique ( `.dll` , `.so` ou `.dylib` ) aux noms de bibliothèque natifs. Sur Linux et macOS, le runtime essaiera également le préen attente `lib` . Ces noms de bibliothèque sont automatiquement recherchés lorsque vous utilisez des API qui chargent des bibliothèques non managées (par exemple, <xref:System.Runtime.InteropServices.DllImportAttribute> ).

> [!NOTE]
> Les chemins absolus dans les noms de bibliothèque (par exemple, `/usr/lib/libc` ) sont traités tels quels et aucune recherche n’est effectuée.

Prenons l’exemple suivant pour utiliser P/Invoke :

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

Lors de l’exécution sous Windows, la DLL est recherchée dans l’ordre suivant :

1. `nativedep`
1. `nativedep.dll` (si le nom de la bibliothèque ne se termine pas encore par `.dll` ou. `exe` )

En cas d’exécution sur Linux ou macOS, le runtime essaiera d’utiliser `lib` l’extension de la bibliothèque partagée canonique et de l’ajouter. Sur ces systèmes d’exploitation, les variantes de nom de bibliothèque sont essayées dans l’ordre suivant :

1. `nativedep.so` / `nativedep.dylib`
1. `libnativedep.so` / `libnativedep.dylib`<sup>1</sup>
1. `nativedep`
1. `libnativedep` <sup>1</sup>

Sur Linux, l’ordre de recherche est différent si le nom de la bibliothèque se termine par `.so` ou contient `.so.` (Notez la fin `.` ). Prenons l’exemple suivant :

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

Dans ce cas, les variantes du nom de la bibliothèque sont essayées dans l’ordre suivant :

1. `nativedep.so.6`
1. `libnativedep.so.6` <sup>1</sup>
1. `nativedep.so.6.so`
1. `libnativedep.so.6.so` <sup>1</sup>

<sup>1</sup> le chemin d’accès est vérifié uniquement si le nom de la bibliothèque ne contient pas de caractère de séparation de répertoire ( `/` ).

## <a name="custom-import-resolver"></a>Programme de résolution des importations personnalisé

Dans des scénarios plus complexes, vous pouvez utiliser <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> pour résoudre les importations de dll au moment de l’exécution. Dans l’exemple suivant, `nativedep` est résolu en `nativedep_avx2` si l’UC la prend en charge.

> [!TIP]
> Cette fonctionnalité est disponible uniquement dans .NET 5 et .NET Core 3,1 ou version ultérieure.

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a>Voir aussi

- [Appel de code non managé (P/Invoke)](pinvoke.md)
