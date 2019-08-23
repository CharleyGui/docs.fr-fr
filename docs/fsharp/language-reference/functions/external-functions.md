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
# <a name="external-functions"></a><span data-ttu-id="7c726-103">Fonctions externes</span><span class="sxs-lookup"><span data-stu-id="7c726-103">External Functions</span></span>

<span data-ttu-id="7c726-104">Cette rubrique décrit F# la prise en charge linguistique pour l’appel de fonctions en code natif.</span><span class="sxs-lookup"><span data-stu-id="7c726-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c726-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c726-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="7c726-106">Notes</span><span class="sxs-lookup"><span data-stu-id="7c726-106">Remarks</span></span>

<span data-ttu-id="7c726-107">Dans la syntaxe précédente, les *arguments* représentent les arguments fournis à l' `System.Runtime.InteropServices.DllImportAttribute` attribut.</span><span class="sxs-lookup"><span data-stu-id="7c726-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="7c726-108">Le premier argument est une chaîne qui représente le nom de la DLL qui contient cette fonction, sans l’extension. dll.</span><span class="sxs-lookup"><span data-stu-id="7c726-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="7c726-109">Des arguments supplémentaires peuvent être fournis pour toutes les propriétés publiques de la `System.Runtime.InteropServices.DllImportAttribute` classe, telles que la Convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="7c726-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="7c726-110">Supposons que vous avez C++ une DLL native qui contient la fonction exportée suivante.</span><span class="sxs-lookup"><span data-stu-id="7c726-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="7c726-111">Vous pouvez appeler cette fonction à F# partir de à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="7c726-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="7c726-112">L’interopérabilité avec le code natif est appelée *appel* de code non managé et est une fonctionnalité du CLR.</span><span class="sxs-lookup"><span data-stu-id="7c726-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="7c726-113">Pour plus d’informations, consultez [Interopération avec du code non managé](../../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c726-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="7c726-114">Les informations contenues dans cette section s' F#appliquent à.</span><span class="sxs-lookup"><span data-stu-id="7c726-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c726-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c726-115">See also</span></span>

- [<span data-ttu-id="7c726-116">Fonctions</span><span class="sxs-lookup"><span data-stu-id="7c726-116">Functions</span></span>](index.md)
