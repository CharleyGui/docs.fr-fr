---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581416"
---
# <a name="-optioncompare"></a><span data-ttu-id="69e4a-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="69e4a-102">-optioncompare</span></span>

<span data-ttu-id="69e4a-103">Spécifie la façon dont sont effectuées les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="69e4a-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="69e4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69e4a-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="69e4a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="69e4a-105">Remarks</span></span>

<span data-ttu-id="69e4a-106">Vous pouvez spécifier `-optioncompare` dans l’une des deux formes `-optioncompare:binary` suivantes : pour utiliser des comparaisons de `-optioncompare:text` chaînes binaires et pour utiliser des comparaisons de chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="69e4a-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="69e4a-107">Par défaut, le compilateur utilise `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="69e4a-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="69e4a-108">Dans Microsoft Windows, la page de codes actuelle détermine l’ordre de tri binaire.</span><span class="sxs-lookup"><span data-stu-id="69e4a-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="69e4a-109">Un ordre de tri binaire standard est le suivant :</span><span class="sxs-lookup"><span data-stu-id="69e4a-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="69e4a-110">Les comparaisons de chaînes basées sur du texte sont basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="69e4a-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="69e4a-111">Un ordre de tri de texte classique est le suivant :</span><span class="sxs-lookup"><span data-stu-id="69e4a-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="69e4a-112">Pour définir-optioncompare dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69e4a-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="69e4a-113">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="69e4a-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="69e4a-114">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="69e4a-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="69e4a-115">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="69e4a-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="69e4a-116">Modifiez la valeur dans la zone **option compare** .</span><span class="sxs-lookup"><span data-stu-id="69e4a-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="69e4a-117">Pour définir-optioncompare par programmation</span><span class="sxs-lookup"><span data-stu-id="69e4a-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="69e4a-118">Consultez [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69e4a-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="69e4a-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="69e4a-119">Example</span></span>

<span data-ttu-id="69e4a-120">Le code suivant compile `ProjFile.vb` et utilise des comparaisons de chaînes binaires.</span><span class="sxs-lookup"><span data-stu-id="69e4a-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="69e4a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69e4a-121">See also</span></span>

- [<span data-ttu-id="69e4a-122">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69e4a-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="69e4a-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="69e4a-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="69e4a-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="69e4a-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="69e4a-125">-optioninfer (</span><span class="sxs-lookup"><span data-stu-id="69e4a-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="69e4a-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="69e4a-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="69e4a-127">Option Compare (instruction)</span><span class="sxs-lookup"><span data-stu-id="69e4a-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="69e4a-128">Valeurs par défaut VB, Projets, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="69e4a-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
