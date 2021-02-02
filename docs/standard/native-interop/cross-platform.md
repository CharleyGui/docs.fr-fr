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
# <a name="writing-cross-platform-pinvoke-code"></a><span data-ttu-id="d29f8-104">Écriture de code P/Invoke multiplateforme</span><span class="sxs-lookup"><span data-stu-id="d29f8-104">Writing cross platform P/Invoke code</span></span>

## <a name="library-name-variations"></a><span data-ttu-id="d29f8-105">Variantes de nom de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="d29f8-105">Library name variations</span></span>

<span data-ttu-id="d29f8-106">Pour faciliter le code P/Invoke Cross-Platform plus simple, le runtime ajoute l’extension de bibliothèque partagée canonique ( `.dll` , `.so` ou `.dylib` ) aux noms de bibliothèque natifs.</span><span class="sxs-lookup"><span data-stu-id="d29f8-106">To facilitate simpler cross platform P/Invoke code, the runtime adds the canonical shared library extension (`.dll`, `.so` or `.dylib`) to native library names.</span></span> <span data-ttu-id="d29f8-107">Sur Linux et macOS, le runtime essaiera également le préen attente `lib` .</span><span class="sxs-lookup"><span data-stu-id="d29f8-107">On Linux and macOS, the runtime will also try prepending `lib`.</span></span> <span data-ttu-id="d29f8-108">Ces noms de bibliothèque sont automatiquement recherchés lorsque vous utilisez des API qui chargent des bibliothèques non managées (par exemple, <xref:System.Runtime.InteropServices.DllImportAttribute> ).</span><span class="sxs-lookup"><span data-stu-id="d29f8-108">These library names variations are automatically searched when you use APIs that load unmanaged libraries (e.g., <xref:System.Runtime.InteropServices.DllImportAttribute>).</span></span>

> [!NOTE]
> <span data-ttu-id="d29f8-109">Les chemins absolus dans les noms de bibliothèque (par exemple, `/usr/lib/libc` ) sont traités tels quels et aucune recherche n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="d29f8-109">Absolute paths in library names (e.g., `/usr/lib/libc`) are treated as-is and no variations will be searched.</span></span>

<span data-ttu-id="d29f8-110">Prenons l’exemple suivant pour utiliser P/Invoke :</span><span class="sxs-lookup"><span data-stu-id="d29f8-110">Consider the following example of using P/Invoke:</span></span>

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

<span data-ttu-id="d29f8-111">Lors de l’exécution sous Windows, la DLL est recherchée dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="d29f8-111">When running on Windows, the DLL is searched for in the following order:</span></span>

1. `nativedep`
1. <span data-ttu-id="d29f8-112">`nativedep.dll` (si le nom de la bibliothèque ne se termine pas encore par `.dll` ou. `exe` )</span><span class="sxs-lookup"><span data-stu-id="d29f8-112">`nativedep.dll` (if the library name does not already end with `.dll` or .`exe`)</span></span>

<span data-ttu-id="d29f8-113">En cas d’exécution sur Linux ou macOS, le runtime essaiera d’utiliser `lib` l’extension de la bibliothèque partagée canonique et de l’ajouter.</span><span class="sxs-lookup"><span data-stu-id="d29f8-113">When running on Linux or macOS, the runtime will try prepending `lib` and appending the canonical shared library extension.</span></span> <span data-ttu-id="d29f8-114">Sur ces systèmes d’exploitation, les variantes de nom de bibliothèque sont essayées dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="d29f8-114">On these OSes, library name variations are tried in the following order:</span></span>

1. `nativedep.so` / `nativedep.dylib`
1. <span data-ttu-id="d29f8-115">`libnativedep.so` / `libnativedep.dylib`<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d29f8-115">`libnativedep.so` / `libnativedep.dylib` <sup>1</sup></span></span>
1. `nativedep`
1. <span data-ttu-id="d29f8-116">`libnativedep` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d29f8-116">`libnativedep` <sup>1</sup></span></span>

<span data-ttu-id="d29f8-117">Sur Linux, l’ordre de recherche est différent si le nom de la bibliothèque se termine par `.so` ou contient `.so.` (Notez la fin `.` ).</span><span class="sxs-lookup"><span data-stu-id="d29f8-117">On Linux, the search order is different if the library name ends with `.so` or contains `.so.` (note the trailing `.`).</span></span> <span data-ttu-id="d29f8-118">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d29f8-118">Consider the following example:</span></span>

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

<span data-ttu-id="d29f8-119">Dans ce cas, les variantes du nom de la bibliothèque sont essayées dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="d29f8-119">In this case, the library name variations are tried in the following order:</span></span>

1. `nativedep.so.6`
1. <span data-ttu-id="d29f8-120">`libnativedep.so.6` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d29f8-120">`libnativedep.so.6` <sup>1</sup></span></span>
1. `nativedep.so.6.so`
1. <span data-ttu-id="d29f8-121">`libnativedep.so.6.so` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d29f8-121">`libnativedep.so.6.so` <sup>1</sup></span></span>

<span data-ttu-id="d29f8-122"><sup>1</sup> le chemin d’accès est vérifié uniquement si le nom de la bibliothèque ne contient pas de caractère de séparation de répertoire ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="d29f8-122"><sup>1</sup> Path is checked only if the library name does not contain a directory separator character (`/`).</span></span>

## <a name="custom-import-resolver"></a><span data-ttu-id="d29f8-123">Programme de résolution des importations personnalisé</span><span class="sxs-lookup"><span data-stu-id="d29f8-123">Custom import resolver</span></span>

<span data-ttu-id="d29f8-124">Dans des scénarios plus complexes, vous pouvez utiliser <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> pour résoudre les importations de dll au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d29f8-124">In more complex scenarios, you can use <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> to resolve DLL imports at runtime.</span></span> <span data-ttu-id="d29f8-125">Dans l’exemple suivant, `nativedep` est résolu en `nativedep_avx2` si l’UC la prend en charge.</span><span class="sxs-lookup"><span data-stu-id="d29f8-125">In the following example, `nativedep` is resolved to `nativedep_avx2` if the CPU supports it.</span></span>

> [!TIP]
> <span data-ttu-id="d29f8-126">Cette fonctionnalité est disponible uniquement dans .NET 5 et .NET Core 3,1 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d29f8-126">This functionality is only available in .NET 5 and .NET Core 3.1 or later.</span></span>

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="d29f8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d29f8-127">See also</span></span>

- [<span data-ttu-id="d29f8-128">Appel de code non managé (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="d29f8-128">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
