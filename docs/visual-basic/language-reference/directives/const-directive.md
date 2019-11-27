---
title: '#Const, directive'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 278219edb1bb5d1c0bb015611d69cbe4ae70014b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343843"
---
# <a name="const-directive"></a><span data-ttu-id="c8c3a-102">#Const, directive</span><span class="sxs-lookup"><span data-stu-id="c8c3a-102">#Const Directive</span></span>

<span data-ttu-id="c8c3a-103">Définit les constantes conditionnelles du compilateur pour Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8c3a-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c8c3a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c8c3a-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="c8c3a-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-106">Required.</span></span> <span data-ttu-id="c8c3a-107">Nom de la constante définie.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="c8c3a-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-108">Required.</span></span> <span data-ttu-id="c8c3a-109">Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques, à l’exception de `Is`.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8c3a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="c8c3a-110">Remarks</span></span>  

 <span data-ttu-id="c8c3a-111">Les constantes de compilateur conditionnel sont toujours privées pour le fichier dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="c8c3a-112">Vous ne pouvez pas créer de constantes de compilateur publiques à l’aide de la directive `#Const` ; vous pouvez les créer uniquement dans l’interface utilisateur ou avec l’option de compilateur `/define`.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="c8c3a-113">Vous pouvez uniquement utiliser des constantes et des littéraux de compilateur conditionnels dans `expression`.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="c8c3a-114">L’utilisation d’une constante standard définie avec `Const` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="c8c3a-115">À l’inverse, vous pouvez utiliser des constantes définies avec le mot clé `#Const` uniquement pour la compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="c8c3a-116">Les constantes peuvent également être non définies, auquel cas leur valeur est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c3a-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8c3a-117">Example</span></span>  

 <span data-ttu-id="c8c3a-118">Cet exemple utilise la directive `#Const`.</span><span class="sxs-lookup"><span data-stu-id="c8c3a-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c8c3a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8c3a-119">See also</span></span>

- [<span data-ttu-id="c8c3a-120">-définir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8c3a-120">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="c8c3a-121">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="c8c3a-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="c8c3a-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="c8c3a-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="c8c3a-123">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="c8c3a-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="c8c3a-124">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="c8c3a-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
