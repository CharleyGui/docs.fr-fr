---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 028fa148d0e5622648a5fdfff1789c3d0bfde057
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268281"
---
# <a name="-netcf"></a><span data-ttu-id="00814-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="00814-102">-netcf</span></span>

<span data-ttu-id="00814-103">Configure le compilateur pour cibler le .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="00814-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="00814-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00814-104">Syntax</span></span>

```
-netcf
```

## <a name="remarks"></a><span data-ttu-id="00814-105">Notes</span><span class="sxs-lookup"><span data-stu-id="00814-105">Remarks</span></span>

<span data-ttu-id="00814-106">La `-netcf` option, le compilateur Visual Basic cibler le .NET Compact Framework plutôt que le .NET Framework complet.</span><span class="sxs-lookup"><span data-stu-id="00814-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="00814-107">Fonctionnalités de langage qui sont trouve uniquement dans le .NET Framework complet sont désactivée.</span><span class="sxs-lookup"><span data-stu-id="00814-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="00814-108">Le `-netcf` option est conçue pour être utilisée avec [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="00814-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="00814-109">Les fonctionnalités de langage désactivées par `-netcf` sont les mêmes fonctionnalités de langage pas présentes dans les fichiers ciblés avec `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="00814-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="00814-110">Le `-netcf` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="00814-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="00814-111">Le `-netcf` option est définie lorsqu’un projet smart device de Visual Basic est chargé.</span><span class="sxs-lookup"><span data-stu-id="00814-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="00814-112">Le `-netcf` option modifie les fonctionnalités de langage suivantes :</span><span class="sxs-lookup"><span data-stu-id="00814-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="00814-113">Le [fin \<mot clé > instruction](../../../visual-basic/language-reference/statements/end-keyword-statement.md) mot clé, qui termine l’exécution d’un programme, est désactivé.</span><span class="sxs-lookup"><span data-stu-id="00814-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="00814-114">Le programme suivant se compile et s’exécute sans `-netcf` mais échoue au moment de la compilation avec `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="00814-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="00814-115">Liaison tardive dans chacun des formulaires est désactivée.</span><span class="sxs-lookup"><span data-stu-id="00814-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="00814-116">Erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrées.</span><span class="sxs-lookup"><span data-stu-id="00814-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="00814-117">Le programme suivant se compile et s’exécute sans `-netcf` mais échoue au moment de la compilation avec `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="00814-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="00814-118">Le [automatique](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificateurs sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="00814-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="00814-119">La syntaxe de la [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instruction est également modifiée pour `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="00814-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="00814-120">Le code suivant montre l’effet de `-netcf` sur une compilation.</span><span class="sxs-lookup"><span data-stu-id="00814-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="00814-121">À l’aide de mots clés Visual Basic 6.0 qui ont été supprimés à partir de Visual Basic génère une erreur différente lorsque `-netcf` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="00814-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="00814-122">Cela affecte les messages d’erreur pour les mots clés suivants :</span><span class="sxs-lookup"><span data-stu-id="00814-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="00814-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="00814-123">Example</span></span>

<span data-ttu-id="00814-124">Le code suivant compile `Myfile.vb` avec .NET Compact Framework, l’utilisation des versions de mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="00814-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="00814-125">En règle générale, vous utiliseriez la version la plus récente du .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="00814-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="00814-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00814-126">See also</span></span>

- [<span data-ttu-id="00814-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00814-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="00814-128">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="00814-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="00814-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="00814-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
