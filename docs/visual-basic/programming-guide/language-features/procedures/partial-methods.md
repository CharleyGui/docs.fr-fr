---
title: Méthodes partielles
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352637"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="62cbd-102">Méthodes partielles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62cbd-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="62cbd-103">Les méthodes partielles permettent aux développeurs d’insérer une logique personnalisée dans le code.</span><span class="sxs-lookup"><span data-stu-id="62cbd-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="62cbd-104">En règle générale, le code fait partie d’une classe générée par le concepteur.</span><span class="sxs-lookup"><span data-stu-id="62cbd-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="62cbd-105">Les méthodes partielles sont définies dans une classe partielle créée par un générateur de code, et elles sont généralement utilisées pour fournir une notification indiquant qu’un événement a été modifié.</span><span class="sxs-lookup"><span data-stu-id="62cbd-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="62cbd-106">Ils permettent au développeur de spécifier un comportement personnalisé en réponse à la modification.</span><span class="sxs-lookup"><span data-stu-id="62cbd-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="62cbd-107">Le concepteur du générateur de code définit uniquement la signature de la méthode et un ou plusieurs appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="62cbd-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="62cbd-108">Les développeurs peuvent ensuite fournir des implémentations pour la méthode s’ils souhaitent personnaliser le comportement du code généré.</span><span class="sxs-lookup"><span data-stu-id="62cbd-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="62cbd-109">Quand aucune implémentation n’est fournie, les appels à la méthode sont supprimés par le compilateur, ce qui entraîne une surcharge de performance supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="62cbd-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="62cbd-110">Déclaration</span><span class="sxs-lookup"><span data-stu-id="62cbd-110">Declaration</span></span>  
 <span data-ttu-id="62cbd-111">Le code généré marque la définition d’une méthode partielle en plaçant le mot clé `Partial` au début de la ligne de signature.</span><span class="sxs-lookup"><span data-stu-id="62cbd-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="62cbd-112">La définition doit respecter les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="62cbd-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="62cbd-113">La méthode doit être une `Sub`, et non une `Function`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="62cbd-114">Le corps de la méthode doit être laissé vide.</span><span class="sxs-lookup"><span data-stu-id="62cbd-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="62cbd-115">Le modificateur d’accès doit être `Private`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="62cbd-116">Implémentation</span><span class="sxs-lookup"><span data-stu-id="62cbd-116">Implementation</span></span>  
 <span data-ttu-id="62cbd-117">L’implémentation consiste principalement à remplir le corps de la méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="62cbd-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="62cbd-118">L’implémentation est généralement dans une classe partielle distincte de la définition, et est écrite par un développeur qui souhaite étendre le code généré.</span><span class="sxs-lookup"><span data-stu-id="62cbd-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="62cbd-119">L’exemple précédent duplique exactement la signature dans la déclaration, mais les variations sont possibles.</span><span class="sxs-lookup"><span data-stu-id="62cbd-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="62cbd-120">En particulier, d’autres modificateurs peuvent être ajoutés, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="62cbd-121">Un seul modificateur de `Overrides` est autorisé.</span><span class="sxs-lookup"><span data-stu-id="62cbd-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="62cbd-122">Pour plus d’informations sur les modificateurs de méthode, consultez [instruction Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62cbd-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="62cbd-123">Utilisez</span><span class="sxs-lookup"><span data-stu-id="62cbd-123">Use</span></span>  
 <span data-ttu-id="62cbd-124">Vous appelez une méthode partielle comme vous le feriez pour tout autre `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="62cbd-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="62cbd-125">Si la méthode a été implémentée, les arguments sont évalués et le corps de la méthode est exécuté.</span><span class="sxs-lookup"><span data-stu-id="62cbd-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="62cbd-126">Toutefois, n’oubliez pas que l’implémentation d’une méthode partielle est facultative.</span><span class="sxs-lookup"><span data-stu-id="62cbd-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="62cbd-127">Si la méthode n’est pas implémentée, un appel à celle-ci n’a aucun effet, et les expressions passées comme arguments à la méthode ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="62cbd-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62cbd-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="62cbd-128">Example</span></span>  
 <span data-ttu-id="62cbd-129">Dans un fichier nommé Product. Designer. vb, définissez une classe `Product` qui a une propriété `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="62cbd-130">Dans un fichier nommé Product. vb, fournissez une implémentation pour `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="62cbd-131">Enfin, dans la méthode main d’un projet, déclarez une instance de `Product` et fournissez une valeur initiale pour sa propriété `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="62cbd-132">Une boîte de message s’affiche pour afficher le message suivant :</span><span class="sxs-lookup"><span data-stu-id="62cbd-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="62cbd-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62cbd-133">See also</span></span>

- [<span data-ttu-id="62cbd-134">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="62cbd-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="62cbd-135">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="62cbd-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="62cbd-136">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="62cbd-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="62cbd-137">Partial</span><span class="sxs-lookup"><span data-stu-id="62cbd-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="62cbd-138">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="62cbd-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="62cbd-139">Ajout d’une logique métier à l’aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="62cbd-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
