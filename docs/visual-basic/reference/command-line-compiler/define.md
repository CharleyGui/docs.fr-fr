---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: d0d1b03d9ab98f28a0112198f1ecc1e928d6d4a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408710"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="edad2-102">-définir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edad2-102">-define (Visual Basic)</span></span>
<span data-ttu-id="edad2-103">Définit des constantes conditionnelles du compilateur.</span><span class="sxs-lookup"><span data-stu-id="edad2-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edad2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edad2-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="edad2-105">ou</span><span class="sxs-lookup"><span data-stu-id="edad2-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="edad2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="edad2-106">Arguments</span></span>  
  
|<span data-ttu-id="edad2-107">Terme</span><span class="sxs-lookup"><span data-stu-id="edad2-107">Term</span></span>|<span data-ttu-id="edad2-108">Définition</span><span class="sxs-lookup"><span data-stu-id="edad2-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="edad2-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="edad2-109">Required.</span></span> <span data-ttu-id="edad2-110">Symbole à définir.</span><span class="sxs-lookup"><span data-stu-id="edad2-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="edad2-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="edad2-111">Optional.</span></span> <span data-ttu-id="edad2-112">Valeur à affecter au `symbol`.</span><span class="sxs-lookup"><span data-stu-id="edad2-112">The value to assign `symbol`.</span></span> <span data-ttu-id="edad2-113">Si `value` est une chaîne, elle doit être entourée par des barres obliques inverses ou des séquences de guillemets ( \\ ") au lieu de guillemets.</span><span class="sxs-lookup"><span data-stu-id="edad2-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="edad2-114">Si aucune valeur n'est spécifiée, il prend la valeur True.</span><span class="sxs-lookup"><span data-stu-id="edad2-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edad2-115">Notes</span><span class="sxs-lookup"><span data-stu-id="edad2-115">Remarks</span></span>  
 <span data-ttu-id="edad2-116">L'option `-define` revient à utiliser la directive de préprocesseur `#Const` dans votre fichier source, excepté que les constantes définies avec `-define` sont publiques et s'appliquent à tous les fichiers du projet.</span><span class="sxs-lookup"><span data-stu-id="edad2-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="edad2-117">Vous pouvez utiliser les symboles créés par cette option avec la directive `#If`...`Then`...`#Else` pour effectuer une compilation conditionnelle des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="edad2-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="edad2-118">`-d` est la forme abrégée de `-define`.</span><span class="sxs-lookup"><span data-stu-id="edad2-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="edad2-119">Vous pouvez définir plusieurs symboles avec `-define` en utilisant une virgule pour séparer les définitions de symbole.</span><span class="sxs-lookup"><span data-stu-id="edad2-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="edad2-120">Pour définir-define dans l’environnement de développement intégré de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="edad2-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="edad2-121">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="edad2-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="edad2-122">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="edad2-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="edad2-123">2. cliquez sur l’onglet **compiler** .</span><span class="sxs-lookup"><span data-stu-id="edad2-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="edad2-124">3. cliquez sur **avancé**.</span><span class="sxs-lookup"><span data-stu-id="edad2-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="edad2-125">4. modifiez la valeur dans la zone **constantes personnalisées** .</span><span class="sxs-lookup"><span data-stu-id="edad2-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="edad2-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="edad2-126">Example</span></span>  
 <span data-ttu-id="edad2-127">Le code suivant définit deux constantes de compilation conditionnelle, puis les utilise.</span><span class="sxs-lookup"><span data-stu-id="edad2-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="edad2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edad2-128">See also</span></span>

- [<span data-ttu-id="edad2-129">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edad2-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="edad2-130">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="edad2-130">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="edad2-131">#Const directive</span><span class="sxs-lookup"><span data-stu-id="edad2-131">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="edad2-132">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="edad2-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
