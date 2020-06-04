---
title: Commentaires dans le code
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: b50e76b8f832c3a214ca54f97bab8b0b6789ac25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403315"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="17330-102">Commentaires dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17330-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="17330-103">Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire (`'`).</span><span class="sxs-lookup"><span data-stu-id="17330-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="17330-104">Ce symbole indique au compilateur Visual Basic d’ignorer le texte qui le suit ou le *Commentaire*.</span><span class="sxs-lookup"><span data-stu-id="17330-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="17330-105">Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.</span><span class="sxs-lookup"><span data-stu-id="17330-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="17330-106">En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure (ce qu'elle fait).</span><span class="sxs-lookup"><span data-stu-id="17330-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="17330-107">Ceci est utile tant pour l'auteur du code lui-même que pour toute autre personne amenée à consulter le code.</span><span class="sxs-lookup"><span data-stu-id="17330-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="17330-108">Vous devez séparer les détails relatifs à l'implémentation (comment la procédure fait ce qu'elle doit faire) des commentaires décrivant les caractéristiques fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="17330-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="17330-109">Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="17330-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="17330-110">Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière.</span><span class="sxs-lookup"><span data-stu-id="17330-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="17330-111">Ces deux cas sont illustrés par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="17330-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="17330-112">Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci-dessous l'illustre.</span><span class="sxs-lookup"><span data-stu-id="17330-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="17330-113">Recommandations sur le commentaire</span><span class="sxs-lookup"><span data-stu-id="17330-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="17330-114">Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code.</span><span class="sxs-lookup"><span data-stu-id="17330-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="17330-115">Il s’agit de suggestions ; Visual Basic n’applique pas les règles d’ajout de commentaires.</span><span class="sxs-lookup"><span data-stu-id="17330-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="17330-116">Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.</span><span class="sxs-lookup"><span data-stu-id="17330-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="17330-117">Type de commentaire</span><span class="sxs-lookup"><span data-stu-id="17330-117">Comment type</span></span>|<span data-ttu-id="17330-118">Description du commentaire</span><span class="sxs-lookup"><span data-stu-id="17330-118">Comment description</span></span>|  
|<span data-ttu-id="17330-119">Objectif</span><span class="sxs-lookup"><span data-stu-id="17330-119">Purpose</span></span>|<span data-ttu-id="17330-120">Décrit ce que fait la procédure (et non comment elle le fait)</span><span class="sxs-lookup"><span data-stu-id="17330-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="17330-121">Hypothèses</span><span class="sxs-lookup"><span data-stu-id="17330-121">Assumptions</span></span>|<span data-ttu-id="17330-122">Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.</span><span class="sxs-lookup"><span data-stu-id="17330-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="17330-123">Effets</span><span class="sxs-lookup"><span data-stu-id="17330-123">Effects</span></span>|<span data-ttu-id="17330-124">Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets (uniquement si ce n'est pas évident)</span><span class="sxs-lookup"><span data-stu-id="17330-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="17330-125">Entrées</span><span class="sxs-lookup"><span data-stu-id="17330-125">Inputs</span></span>|<span data-ttu-id="17330-126">Spécifie l’objectif attaché à l’argument</span><span class="sxs-lookup"><span data-stu-id="17330-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="17330-127">Retours</span><span class="sxs-lookup"><span data-stu-id="17330-127">Returns</span></span>|<span data-ttu-id="17330-128">Explique les valeurs retournées par la procédure.</span><span class="sxs-lookup"><span data-stu-id="17330-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="17330-129">N'oubliez pas :</span><span class="sxs-lookup"><span data-stu-id="17330-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="17330-130">Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.</span><span class="sxs-lookup"><span data-stu-id="17330-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="17330-131">Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.</span><span class="sxs-lookup"><span data-stu-id="17330-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="17330-132">Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="17330-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="17330-133">Vous pouvez ajouter ou supprimer des symboles de commentaires pour un bloc de code en sélectionnant une ou plusieurs lignes de code et en choisissant le **Commentaire** ( ![ le Visual Basic bouton commentaire dans Visual Studio) et annuler les ](./media/comments-in-code/visual-basic-comment-button.gif) **marques** de commentaire ( ![ le bouton Visual Basic supprimer les marques de commentaire dans Visual Studio ](./media/comments-in-code/visual-basic-uncomment-button.gif) ) de la barre d’outils de **modification** .</span><span class="sxs-lookup"><span data-stu-id="17330-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17330-134">Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`.</span><span class="sxs-lookup"><span data-stu-id="17330-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="17330-135">Toutefois, les boutons supprimer les marques de commentaire des `'` symboles et des **Commentaires** / **Uncomment** sont plus faciles à utiliser et nécessitent moins d’espace et de mémoire.</span><span class="sxs-lookup"><span data-stu-id="17330-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17330-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17330-136">See also</span></span>

- [<span data-ttu-id="17330-137">Instincts de base : documentation de votre code avec des commentaires XML</span><span class="sxs-lookup"><span data-stu-id="17330-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="17330-138">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="17330-138">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="17330-139">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="17330-139">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="17330-140">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="17330-140">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="17330-141">REM (instruction)</span><span class="sxs-lookup"><span data-stu-id="17330-141">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
