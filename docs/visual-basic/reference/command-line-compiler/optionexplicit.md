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
# <a name="-optionexplicit"></a><span data-ttu-id="8b409-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="8b409-102">-optionexplicit</span></span>
<span data-ttu-id="8b409-103">Fait en sorte que le compilateur signale des erreurs si les variables ne sont pas déclarées avant d’être utilisées.</span><span class="sxs-lookup"><span data-stu-id="8b409-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b409-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b409-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b409-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b409-105">Arguments</span></span>  
 <span data-ttu-id="8b409-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8b409-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8b409-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b409-107">Optional.</span></span> <span data-ttu-id="8b409-108">Spécifiez `-optionexplicit+` pour exiger une déclaration explicite de variables.</span><span class="sxs-lookup"><span data-stu-id="8b409-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="8b409-109">L' `-optionexplicit+` option est la valeur par défaut et est identique `-optionexplicit`à.</span><span class="sxs-lookup"><span data-stu-id="8b409-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="8b409-110">L' `-optionexplicit-` option active la déclaration implicite de variables.</span><span class="sxs-lookup"><span data-stu-id="8b409-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b409-111">Notes</span><span class="sxs-lookup"><span data-stu-id="8b409-111">Remarks</span></span>  
 <span data-ttu-id="8b409-112">Si le fichier de code source contient une [instruction Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction remplace le `-optionexplicit` paramètre du compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8b409-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="8b409-113">Pour définir-optionexplicit dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b409-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="8b409-114">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="8b409-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8b409-115">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8b409-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="8b409-116">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="8b409-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="8b409-117">Modifiez la valeur dans la zone **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="8b409-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b409-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b409-118">Example</span></span>  
 <span data-ttu-id="8b409-119">Le code suivant compile lorsque `-optionexplicit-` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8b409-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8b409-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b409-120">See also</span></span>

- [<span data-ttu-id="8b409-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b409-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8b409-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8b409-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="8b409-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="8b409-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="8b409-124">-optioninfer (</span><span class="sxs-lookup"><span data-stu-id="8b409-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="8b409-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="8b409-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="8b409-126">Option Explicit (instruction)</span><span class="sxs-lookup"><span data-stu-id="8b409-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="8b409-127">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="8b409-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
