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
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="2fbe8-103">Identificateurs de ligne, de fichier et de chemin d’accès source</span><span class="sxs-lookup"><span data-stu-id="2fbe8-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="2fbe8-104">Les identificateurs `__LINE__`, `__SOURCE_DIRECTORY__` et `__SOURCE_FILE__` sont des valeurs intégrées qui vous permettent d’accéder au numéro de ligne source, au répertoire et au nom de fichier dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fbe8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fbe8-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="2fbe8-106">Notes</span><span class="sxs-lookup"><span data-stu-id="2fbe8-106">Remarks</span></span>

<span data-ttu-id="2fbe8-107">Chacune de ces valeurs est de `string`type.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="2fbe8-108">Le tableau suivant récapitule les identificateurs de ligne, de fichier et de chemin d’accès source qui F#sont disponibles dans.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="2fbe8-109">Ces identificateurs ne sont pas des macros de préprocesseur; Il s’agit de valeurs intégrées qui sont reconnues par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="2fbe8-110">Identificateur prédéfini</span><span class="sxs-lookup"><span data-stu-id="2fbe8-110">Predefined identifier</span></span>|<span data-ttu-id="2fbe8-111">Description</span><span class="sxs-lookup"><span data-stu-id="2fbe8-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="2fbe8-112">Prend la valeur du numéro de ligne en cours `#line` , en considérant les directives.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="2fbe8-113">Prend la valeur du chemin d’accès complet actuel du répertoire source, `#line` en prenant en compte les directives.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="2fbe8-114">Prend le nom du fichier source actuel, sans son chemin d’accès, `#line` en prenant en compte les directives.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="2fbe8-115">Pour plus d’informations sur `#line` la directive, consultez [directives de compilateur](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="2fbe8-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fbe8-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fbe8-116">Example</span></span>

<span data-ttu-id="2fbe8-117">L’exemple de code suivant illustre l’utilisation de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="2fbe8-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="2fbe8-118">Sortie :</span><span class="sxs-lookup"><span data-stu-id="2fbe8-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="2fbe8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fbe8-119">See also</span></span>

- [<span data-ttu-id="2fbe8-120">Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="2fbe8-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="2fbe8-121">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="2fbe8-121">F# Language Reference</span></span>](index.md)
