---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266727"
---
# <a name="-optionexplicit"></a><span data-ttu-id="305cd-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="305cd-102">-optionexplicit</span></span>
<span data-ttu-id="305cd-103">Le compilateur signale les erreurs si les variables ne sont pas déclarées avant qu’elles ne soient utilisées.</span><span class="sxs-lookup"><span data-stu-id="305cd-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="305cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="305cd-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="305cd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="305cd-105">Arguments</span></span>  
 <span data-ttu-id="305cd-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="305cd-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="305cd-107">facultatif.</span><span class="sxs-lookup"><span data-stu-id="305cd-107">Optional.</span></span> <span data-ttu-id="305cd-108">Spécifier `-optionexplicit+` pour exiger une déclaration explicite des variables.</span><span class="sxs-lookup"><span data-stu-id="305cd-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="305cd-109">L’option `-optionexplicit+` est la valeur `-optionexplicit`par défaut et est la même que .</span><span class="sxs-lookup"><span data-stu-id="305cd-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="305cd-110">L’option `-optionexplicit-` permet la déclaration implicite de variables.</span><span class="sxs-lookup"><span data-stu-id="305cd-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="305cd-111">Notes </span><span class="sxs-lookup"><span data-stu-id="305cd-111">Remarks</span></span>  
 <span data-ttu-id="305cd-112">Si le fichier de code source contient une déclaration `-optionexplicit` Option [Explicite,](../../../visual-basic/language-reference/statements/option-explicit-statement.md)l’instruction remplace le paramètre de compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="305cd-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="305cd-113">Pour définir -optionexplicit dans le Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="305cd-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="305cd-114">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="305cd-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="305cd-115">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="305cd-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="305cd-116">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="305cd-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="305cd-117">Modifier la valeur de la boîte **Option Explicite.**</span><span class="sxs-lookup"><span data-stu-id="305cd-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="305cd-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="305cd-118">Example</span></span>  
 <span data-ttu-id="305cd-119">Le code suivant compile quand `-optionexplicit-` il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="305cd-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="305cd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305cd-120">See also</span></span>

- [<span data-ttu-id="305cd-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="305cd-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="305cd-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="305cd-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="305cd-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="305cd-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="305cd-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="305cd-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="305cd-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="305cd-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="305cd-126">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="305cd-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="305cd-127">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="305cd-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
