---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583075"
---
# <a name="-optionstrict"></a><span data-ttu-id="8aa91-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="8aa91-102">-optionstrict</span></span>

<span data-ttu-id="8aa91-103">Applique la sémantique de type stricte pour restreindre les conversions de types implicites.</span><span class="sxs-lookup"><span data-stu-id="8aa91-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="8aa91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa91-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="8aa91-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8aa91-105">Arguments</span></span>

<span data-ttu-id="8aa91-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8aa91-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="8aa91-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8aa91-107">Optional.</span></span> <span data-ttu-id="8aa91-108">L' `-optionstrict+` option restreint la conversion de type implicite.</span><span class="sxs-lookup"><span data-stu-id="8aa91-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="8aa91-109">La valeur par défaut de cette `-optionstrict-`option est.</span><span class="sxs-lookup"><span data-stu-id="8aa91-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="8aa91-110">L' `-optionstrict+` option est la même que `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="8aa91-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="8aa91-111">Vous pouvez utiliser à la fois pour la sémantique de type permissive.</span><span class="sxs-lookup"><span data-stu-id="8aa91-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="8aa91-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8aa91-112">Required.</span></span> <span data-ttu-id="8aa91-113">Avertir lorsque la sémantique de langue stricte n’est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="8aa91-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="8aa91-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8aa91-114">Remarks</span></span>

<span data-ttu-id="8aa91-115">Lorsque `-optionstrict+` est activé, seules les conversions de type étendue peuvent être effectuées implicitement.</span><span class="sxs-lookup"><span data-stu-id="8aa91-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="8aa91-116">Les conversions de types restrictives implicites, telles que `Decimal` l’assignation d’un objet de type à un objet de type entier, sont signalées comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8aa91-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="8aa91-117">Pour générer des avertissements pour les conversions de types restrictives `-optionstrict:custom`implicites, utilisez.</span><span class="sxs-lookup"><span data-stu-id="8aa91-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="8aa91-118">Utilisez `-nowarn:numberlist` pour ignorer des avertissements particuliers `-warnaserror:numberlist` et traiter des avertissements particuliers comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="8aa91-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="8aa91-119">Pour définir-optionstrict dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8aa91-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="8aa91-120">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="8aa91-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8aa91-121">Dans le menu **projet** , cliquez sur **Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="8aa91-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="8aa91-122">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="8aa91-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="8aa91-123">Modifiez la valeur dans la zone **option strict** .</span><span class="sxs-lookup"><span data-stu-id="8aa91-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="8aa91-124">Pour définir-optionstrict par programmation</span><span class="sxs-lookup"><span data-stu-id="8aa91-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="8aa91-125">Consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8aa91-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="8aa91-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="8aa91-126">Example</span></span>

<span data-ttu-id="8aa91-127">Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.</span><span class="sxs-lookup"><span data-stu-id="8aa91-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="8aa91-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aa91-128">See also</span></span>

- [<span data-ttu-id="8aa91-129">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8aa91-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8aa91-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8aa91-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="8aa91-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="8aa91-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="8aa91-132">-optioninfer (</span><span class="sxs-lookup"><span data-stu-id="8aa91-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="8aa91-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="8aa91-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="8aa91-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8aa91-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="8aa91-135">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="8aa91-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="8aa91-136">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="8aa91-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="8aa91-137">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="8aa91-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
