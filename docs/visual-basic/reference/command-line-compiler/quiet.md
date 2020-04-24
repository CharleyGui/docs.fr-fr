---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005278"
---
# <a name="-quiet"></a><span data-ttu-id="a6a73-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="a6a73-102">-quiet</span></span>

<span data-ttu-id="a6a73-103">Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a6a73-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6a73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6a73-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="a6a73-105">Notes</span><span class="sxs-lookup"><span data-stu-id="a6a73-105">Remarks</span></span>

<span data-ttu-id="a6a73-106">Par défaut, l'option `-quiet` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="a6a73-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="a6a73-107">Lorsque le compilateur signale une erreur ou un avertissement lié à la syntaxe, il renvoie également la ligne à partir du code source.</span><span class="sxs-lookup"><span data-stu-id="a6a73-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="a6a73-108">Pour les applications qui analysent la sortie du compilateur, il peut être plus commode pour le compilateur de générer uniquement le texte du diagnostic.</span><span class="sxs-lookup"><span data-stu-id="a6a73-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="a6a73-109">Dans l’exemple suivant, `Module1` génère une erreur qui comprend le code source lorsqu’elle `-quiet`est compilée sans.</span><span class="sxs-lookup"><span data-stu-id="a6a73-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="a6a73-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="a6a73-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="a6a73-111">Compilé avec `-quiet`, le compilateur génère uniquement les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a6a73-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="a6a73-112">L' `-quiet` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a6a73-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a6a73-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a6a73-113">Example</span></span>

<span data-ttu-id="a6a73-114">Le code suivant compile `T2.vb` et n’affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="a6a73-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a6a73-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6a73-115">See also</span></span>

- [<span data-ttu-id="a6a73-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6a73-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a6a73-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="a6a73-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
