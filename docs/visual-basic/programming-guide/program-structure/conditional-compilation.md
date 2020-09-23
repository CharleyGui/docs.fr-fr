---
title: Compilation conditionnelle
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098967"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="c6c3a-102">Compilation conditionnelle en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6c3a-102">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="c6c3a-103">Dans la *compilation conditionnelle*, les blocs de code particuliers d’un programme sont compilés de manière sélective, tandis que d’autres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="c6c3a-104">Par exemple, vous pouvez écrire des instructions de débogage qui comparent la vitesse des différentes approches de la même tâche de programmation, ou vous pouvez souhaiter localiser une application pour plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="c6c3a-105">Les instructions de compilation conditionnelle sont conçues pour s’exécuter pendant la compilation, et non au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="c6c3a-106">Vous désignez des blocs de code à compiler de façon conditionnelle avec la `#If...Then...#Else` directive.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="c6c3a-107">Par exemple, pour créer des versions en français et en allemand de la même application à partir du même code source, vous incorporez des segments de code spécifiques à la plateforme dans des `#If...Then` instructions à l’aide des constantes prédéfinies `FrenchVersion` et `GermanVersion` .</span><span class="sxs-lookup"><span data-stu-id="c6c3a-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="c6c3a-108">L’exemple suivant montre comment :</span><span class="sxs-lookup"><span data-stu-id="c6c3a-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c6c3a-109">Si vous affectez à la valeur de la `FrenchVersion` constante de compilation conditionnelle la valeur `True` au moment de la compilation, le code conditionnel de la version française est compilé.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="c6c3a-110">Si vous affectez `GermanVersion` à la constante la valeur `True` , le compilateur utilise la version allemande.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="c6c3a-111">Si aucun n’a `True` la valeur, le code du dernier `Else` bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6c3a-112">La saisie semi-automatique ne fonctionne pas lors de la modification du code et de l’utilisation de directives de compilation conditionnelle si le code ne fait pas partie de la branche active.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="c6c3a-113">Déclaration des constantes de compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="c6c3a-113">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="c6c3a-114">Vous pouvez définir des constantes de compilation conditionnelle de l’une des trois façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6c3a-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="c6c3a-115">Dans le **Concepteur de projets**</span><span class="sxs-lookup"><span data-stu-id="c6c3a-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="c6c3a-116">Au niveau de la ligne de commande lors de l’utilisation du compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c6c3a-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="c6c3a-117">Dans votre code</span><span class="sxs-lookup"><span data-stu-id="c6c3a-117">In your code</span></span>  
  
 <span data-ttu-id="c6c3a-118">Les constantes de compilation conditionnelle ont une portée spéciale et ne sont pas accessibles à partir du code standard.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="c6c3a-119">La portée d’une constante de compilation conditionnelle dépend de la façon dont elle est définie.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="c6c3a-120">Le tableau suivant répertorie l’étendue des constantes déclarées à l’aide de chacune des trois méthodes mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="c6c3a-121">Définition de la constante</span><span class="sxs-lookup"><span data-stu-id="c6c3a-121">How constant is set</span></span>|<span data-ttu-id="c6c3a-122">Étendue de la constante</span><span class="sxs-lookup"><span data-stu-id="c6c3a-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="c6c3a-123">**Concepteur de projets**</span><span class="sxs-lookup"><span data-stu-id="c6c3a-123">**Project Designer**</span></span>|<span data-ttu-id="c6c3a-124">Public pour tous les fichiers du projet</span><span class="sxs-lookup"><span data-stu-id="c6c3a-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="c6c3a-125">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c6c3a-125">Command line</span></span>|<span data-ttu-id="c6c3a-126">Public pour tous les fichiers passés au compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c6c3a-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="c6c3a-127">`#Const` instruction dans le code</span><span class="sxs-lookup"><span data-stu-id="c6c3a-127">`#Const` statement in code</span></span>|<span data-ttu-id="c6c3a-128">Privé pour le fichier dans lequel il est déclaré</span><span class="sxs-lookup"><span data-stu-id="c6c3a-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="c6c3a-129">Pour définir des constantes dans le concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="c6c3a-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="c6c3a-130">-Avant de créer votre fichier exécutable, définissez les constantes dans le **Concepteur de projet** en suivant les étapes indiquées dans [gestion des propriétés de projet et de solution](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="c6c3a-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="c6c3a-131">Pour définir des constantes au niveau de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="c6c3a-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="c6c3a-132">-Utilisez le commutateur **-d** pour entrer des constantes de compilation conditionnelle, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c6c3a-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="c6c3a-133">Aucun espace n’est requis entre le commutateur **-d** et la première constante.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="c6c3a-134">Pour plus d’informations, consultez [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3a-134">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="c6c3a-135">Les déclarations de ligne de commande remplacent les déclarations entrées dans le **Concepteur de projet**, mais ne les efface pas.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="c6c3a-136">Les arguments définis dans le **Concepteur de projets** restent en vigueur pour les compilations suivantes.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="c6c3a-137">Lors de l’écriture de constantes dans le code lui-même, il n’existe pas de règles strictes quant à leur position, car leur étendue est le module entier dans lequel elles sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="c6c3a-138">Pour définir des constantes dans votre code</span><span class="sxs-lookup"><span data-stu-id="c6c3a-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="c6c3a-139">-Placez les constantes dans le bloc de déclaration du module dans lequel elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="c6c3a-140">Cela permet d’organiser votre code et de le rendre plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="c6c3a-141">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c6c3a-141">Related Topics</span></span>  
  
|<span data-ttu-id="c6c3a-142">Intitulé</span><span class="sxs-lookup"><span data-stu-id="c6c3a-142">Title</span></span>|<span data-ttu-id="c6c3a-143">Description</span><span class="sxs-lookup"><span data-stu-id="c6c3a-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="c6c3a-144">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="c6c3a-144">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="c6c3a-145">Fournit des suggestions pour faciliter la lecture et la maintenance de votre code.</span><span class="sxs-lookup"><span data-stu-id="c6c3a-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c6c3a-146">Référence</span><span class="sxs-lookup"><span data-stu-id="c6c3a-146">Reference</span></span>  

 [<span data-ttu-id="c6c3a-147">#Const directive</span><span class="sxs-lookup"><span data-stu-id="c6c3a-147">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="c6c3a-148">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="c6c3a-148">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="c6c3a-149">-définir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6c3a-149">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
