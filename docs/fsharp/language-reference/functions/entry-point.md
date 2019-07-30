---
title: Point d'entrée
description: Découvrez comment définir le point d’entrée sur un F# programme compilé comme fichier exécutable, où l’exécution démarre formellement.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630520"
---
# <a name="entry-point"></a><span data-ttu-id="c44d7-103">Point d'entrée</span><span class="sxs-lookup"><span data-stu-id="c44d7-103">Entry Point</span></span>

<span data-ttu-id="c44d7-104">Cette rubrique décrit la méthode que vous utilisez pour définir le point d’entrée sur F# un programme.</span><span class="sxs-lookup"><span data-stu-id="c44d7-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="c44d7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c44d7-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="c44d7-106">Notes</span><span class="sxs-lookup"><span data-stu-id="c44d7-106">Remarks</span></span>

<span data-ttu-id="c44d7-107">Dans la syntaxe précédente, *let-function-binding* est la définition d’une fonction dans `let` une liaison.</span><span class="sxs-lookup"><span data-stu-id="c44d7-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="c44d7-108">Le point d’entrée d’un programme compilé comme fichier exécutable est l’emplacement où l’exécution démarre formellement.</span><span class="sxs-lookup"><span data-stu-id="c44d7-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="c44d7-109">Vous spécifiez le point d’entrée F# d’une application en `EntryPoint` appliquant l’attribut à `main` la fonction du programme.</span><span class="sxs-lookup"><span data-stu-id="c44d7-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="c44d7-110">Cette fonction (créée à l’aide `let` d’une liaison) doit être la dernière fonction du dernier fichier compilé.</span><span class="sxs-lookup"><span data-stu-id="c44d7-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="c44d7-111">Le dernier fichier compilé est le dernier fichier du projet ou le dernier fichier passé à la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c44d7-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="c44d7-112">La fonction de point d’entrée `string array -> int`a le type.</span><span class="sxs-lookup"><span data-stu-id="c44d7-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="c44d7-113">Les arguments fournis sur la ligne de commande sont passés à `main` la fonction dans le tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c44d7-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="c44d7-114">Le premier élément du tableau est le premier argument; le nom du fichier exécutable n’est pas inclus dans le tableau, comme c’est le cas dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="c44d7-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="c44d7-115">La valeur de retour est utilisée comme code de sortie pour le processus.</span><span class="sxs-lookup"><span data-stu-id="c44d7-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="c44d7-116">Zéro indique généralement une réussite; une valeur différente de zéro indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="c44d7-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="c44d7-117">Il n’existe aucune convention pour la signification spécifique des codes de retour autres que zéro; les significations des codes de retour sont spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="c44d7-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="c44d7-118">L’exemple suivant illustre une fonction simple `main` .</span><span class="sxs-lookup"><span data-stu-id="c44d7-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="c44d7-119">Lorsque ce code est exécuté avec la ligne `EntryPoint.exe 1 2 3`de commande, la sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="c44d7-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="c44d7-120">Point d’entrée implicite</span><span class="sxs-lookup"><span data-stu-id="c44d7-120">Implicit Entry Point</span></span>

<span data-ttu-id="c44d7-121">Lorsqu’un programme n’a pas d’attribut **entryPoint** qui indique explicitement le point d’entrée, les liaisons de niveau supérieur dans le dernier fichier à compiler sont utilisées comme point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c44d7-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="c44d7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c44d7-122">See also</span></span>

- [<span data-ttu-id="c44d7-123">Fonctions</span><span class="sxs-lookup"><span data-stu-id="c44d7-123">Functions</span></span>](index.md)
- [<span data-ttu-id="c44d7-124">Liaisons let</span><span class="sxs-lookup"><span data-stu-id="c44d7-124">let Bindings</span></span>](let-bindings.md)
