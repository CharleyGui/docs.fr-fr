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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400537"
---
# <a name="-optionstrict"></a><span data-ttu-id="47116-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="47116-102">-optionstrict</span></span>

<span data-ttu-id="47116-103">Applique la sémantique de type stricte pour restreindre les conversions de types implicites.</span><span class="sxs-lookup"><span data-stu-id="47116-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="47116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47116-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="47116-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="47116-105">Arguments</span></span>

<span data-ttu-id="47116-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="47116-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="47116-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="47116-107">Optional.</span></span> <span data-ttu-id="47116-108">L' `-optionstrict+` option restreint la conversion de type implicite.</span><span class="sxs-lookup"><span data-stu-id="47116-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="47116-109">La valeur par défaut de cette option est `-optionstrict-` .</span><span class="sxs-lookup"><span data-stu-id="47116-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="47116-110">L' `-optionstrict+` option est la même que `-optionstrict` .</span><span class="sxs-lookup"><span data-stu-id="47116-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="47116-111">Vous pouvez utiliser à la fois pour la sémantique de type permissive.</span><span class="sxs-lookup"><span data-stu-id="47116-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="47116-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="47116-112">Required.</span></span> <span data-ttu-id="47116-113">Avertir lorsque la sémantique de langue stricte n’est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="47116-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="47116-114">Notes</span><span class="sxs-lookup"><span data-stu-id="47116-114">Remarks</span></span>

<span data-ttu-id="47116-115">Lorsque `-optionstrict+` est activé, seules les conversions de type étendue peuvent être effectuées implicitement.</span><span class="sxs-lookup"><span data-stu-id="47116-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="47116-116">Les conversions de types restrictives implicites, telles que l’assignation d’un `Decimal` objet de type à un objet de type entier, sont signalées comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="47116-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="47116-117">Pour générer des avertissements pour les conversions de types restrictives implicites, utilisez `-optionstrict:custom` .</span><span class="sxs-lookup"><span data-stu-id="47116-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="47116-118">Utilisez `-nowarn:numberlist` pour ignorer des avertissements particuliers et `-warnaserror:numberlist` traiter des avertissements particuliers comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="47116-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="47116-119">Pour définir-optionstrict dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47116-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="47116-120">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="47116-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="47116-121">Dans le menu **projet** , cliquez sur **Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="47116-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="47116-122">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="47116-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="47116-123">Modifiez la valeur dans la zone **option strict** .</span><span class="sxs-lookup"><span data-stu-id="47116-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="47116-124">Pour définir-optionstrict par programmation</span><span class="sxs-lookup"><span data-stu-id="47116-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="47116-125">Consultez [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47116-125">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="47116-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="47116-126">Example</span></span>

<span data-ttu-id="47116-127">Le code suivant compile `Test.vb` à l’aide de la sémantique de type stricte.</span><span class="sxs-lookup"><span data-stu-id="47116-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="47116-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47116-128">See also</span></span>

- [<span data-ttu-id="47116-129">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47116-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="47116-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="47116-130">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="47116-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="47116-131">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="47116-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="47116-132">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="47116-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="47116-133">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="47116-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47116-134">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="47116-135">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="47116-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="47116-136">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="47116-136">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="47116-137">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="47116-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
