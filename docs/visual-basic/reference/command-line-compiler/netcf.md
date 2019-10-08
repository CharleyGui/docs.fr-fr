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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005452"
---
# <a name="-netcf"></a><span data-ttu-id="572a4-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="572a4-102">-netcf</span></span>

<span data-ttu-id="572a4-103">Définit le compilateur pour cibler le .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="572a4-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="572a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="572a4-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="572a4-105">Notes</span><span class="sxs-lookup"><span data-stu-id="572a4-105">Remarks</span></span>

<span data-ttu-id="572a4-106">L’option `-netcf` force le compilateur Visual Basic à cibler le .NET Compact Framework plutôt que le .NET Framework complet.</span><span class="sxs-lookup"><span data-stu-id="572a4-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="572a4-107">La fonctionnalité de langage qui est présente uniquement dans le .NET Framework complet est désactivée.</span><span class="sxs-lookup"><span data-stu-id="572a4-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="572a4-108">L’option `-netcf` est conçue pour être utilisée avec [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="572a4-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="572a4-109">Les fonctionnalités de langage désactivées par `-netcf` sont les mêmes fonctionnalités de langage qui ne sont pas présentes dans les fichiers ciblés avec `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="572a4-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="572a4-110">L’option `-netcf` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="572a4-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="572a4-111">L’option `-netcf` est définie lors du chargement d’un projet d’appareil Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="572a4-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="572a4-112">L’option `-netcf` modifie les fonctionnalités de langage suivantes :</span><span class="sxs-lookup"><span data-stu-id="572a4-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="572a4-113">L' [instruction End \<keyword >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) mot clé, qui termine l’exécution d’un programme, est désactivée.</span><span class="sxs-lookup"><span data-stu-id="572a4-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="572a4-114">Le programme suivant compile et s’exécute sans `-netcf`, mais échoue au moment de la compilation avec `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="572a4-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="572a4-115">La liaison tardive, dans tous les formulaires, est désactivée.</span><span class="sxs-lookup"><span data-stu-id="572a4-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="572a4-116">Des erreurs de compilation sont générées lorsque des scénarios de liaison tardive reconnus sont rencontrés.</span><span class="sxs-lookup"><span data-stu-id="572a4-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="572a4-117">Le programme suivant compile et s’exécute sans `-netcf`, mais échoue au moment de la compilation avec `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="572a4-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="572a4-118">Les modificateurs [auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="572a4-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="572a4-119">La syntaxe de l’instruction [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) est également modifiée en `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="572a4-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="572a4-120">Le code suivant illustre l’effet de `-netcf` sur une compilation.</span><span class="sxs-lookup"><span data-stu-id="572a4-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="572a4-121">L’utilisation des mots clés Visual Basic 6,0 qui ont été supprimés de Visual Basic génère une erreur différente lorsque `-netcf` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="572a4-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="572a4-122">Cela affecte les messages d’erreur pour les mots clés suivants :</span><span class="sxs-lookup"><span data-stu-id="572a4-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="572a4-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="572a4-123">Example</span></span>

<span data-ttu-id="572a4-124">Le code suivant compile `Myfile.vb` avec le .NET Compact Framework, à l’aide des versions de mscorlib. dll et de Microsoft. VisualBasic. dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="572a4-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="572a4-125">En règle générale, vous utilisez la version la plus récente du .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="572a4-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="572a4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="572a4-126">See also</span></span>

- [<span data-ttu-id="572a4-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="572a4-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="572a4-128">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="572a4-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="572a4-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="572a4-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
