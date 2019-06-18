---
title: Identificateurs de ligne, de fichier et de chemin d’accès source
description: Découvrez comment utiliser intégrée F# valeurs d’identificateur qui vous permettent d’accéder à la source de ligne numéro, directory et nom de fichier dans votre code.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152049"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="4fbf7-103">Identificateurs de ligne, de fichier et de chemin d’accès source</span><span class="sxs-lookup"><span data-stu-id="4fbf7-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="4fbf7-104">Les identificateurs `__LINE__`, `__SOURCE_DIRECTORY__` et `__SOURCE_FILE__` sont des valeurs intégrées qui vous permettent d’accéder à la ligne numéro, répertoire et fichier nom source dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fbf7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fbf7-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="4fbf7-106">Notes</span><span class="sxs-lookup"><span data-stu-id="4fbf7-106">Remarks</span></span>

<span data-ttu-id="4fbf7-107">Chacune de ces valeurs a le type `string`.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="4fbf7-108">Le tableau suivant récapitule les identificateurs de ligne, de fichier et chemin d’accès source qui sont disponibles dans F#.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="4fbf7-109">Ces identificateurs ne sont pas des macros de préprocesseur ; ils sont des valeurs intégrées qui sont reconnus par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="4fbf7-110">Identificateur prédéfini</span><span class="sxs-lookup"><span data-stu-id="4fbf7-110">Predefined identifier</span></span>|<span data-ttu-id="4fbf7-111">Description</span><span class="sxs-lookup"><span data-stu-id="4fbf7-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="4fbf7-112">Prend la valeur de numéro de ligne en cours, vous envisagez `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="4fbf7-113">Prend la valeur actuelle chemin d’accès complet du répertoire source, envisagez `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="4fbf7-114">Prend la valeur du nom de fichier source actuel, sans son chemin d’accès, vous envisagez `#line` directives.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="4fbf7-115">Pour plus d’informations sur la `#line` directive, consultez [Directives de compilateur](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="4fbf7-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="4fbf7-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="4fbf7-116">Example</span></span>

<span data-ttu-id="4fbf7-117">L’exemple de code suivant illustre l’utilisation de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4fbf7-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="4fbf7-118">Sortie :</span><span class="sxs-lookup"><span data-stu-id="4fbf7-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="4fbf7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fbf7-119">See also</span></span>

- [<span data-ttu-id="4fbf7-120">Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="4fbf7-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="4fbf7-121">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="4fbf7-121">F# Language Reference</span></span>](index.md)
