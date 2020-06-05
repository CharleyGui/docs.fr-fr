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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415464"
---
# <a name="const-directive"></a><span data-ttu-id="0cd03-102">#Const, directive</span><span class="sxs-lookup"><span data-stu-id="0cd03-102">#Const Directive</span></span>

<span data-ttu-id="0cd03-103">Définit les constantes conditionnelles du compilateur pour Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0cd03-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cd03-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0cd03-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="0cd03-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="0cd03-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0cd03-106">Required.</span></span> <span data-ttu-id="0cd03-107">Nom de la constante définie.</span><span class="sxs-lookup"><span data-stu-id="0cd03-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="0cd03-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0cd03-108">Required.</span></span> <span data-ttu-id="0cd03-109">Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques, à l’exception de `Is` .</span><span class="sxs-lookup"><span data-stu-id="0cd03-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cd03-110">Notes</span><span class="sxs-lookup"><span data-stu-id="0cd03-110">Remarks</span></span>  

 <span data-ttu-id="0cd03-111">Les constantes de compilateur conditionnel sont toujours privées pour le fichier dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="0cd03-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="0cd03-112">Vous ne pouvez pas créer de constantes de compilateur publiques à l’aide de la `#Const` directive ; vous pouvez les créer uniquement dans l’interface utilisateur ou avec l' `/define` option de compilateur.</span><span class="sxs-lookup"><span data-stu-id="0cd03-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="0cd03-113">Vous pouvez utiliser uniquement des constantes et des littéraux de compilateur conditionnels dans `expression` .</span><span class="sxs-lookup"><span data-stu-id="0cd03-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="0cd03-114">L’utilisation d’une constante standard définie avec `Const` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="0cd03-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="0cd03-115">À l’inverse, vous pouvez utiliser des constantes définies avec le `#Const` mot clé uniquement pour la compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="0cd03-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="0cd03-116">Les constantes peuvent également être non définies. dans ce cas, elles ont la valeur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0cd03-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cd03-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cd03-117">Example</span></span>  

 <span data-ttu-id="0cd03-118">Cet exemple utilise la directive `#Const`.</span><span class="sxs-lookup"><span data-stu-id="0cd03-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0cd03-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cd03-119">See also</span></span>

- [<span data-ttu-id="0cd03-120">-définir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cd03-120">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="0cd03-121">#If... Then... #Else directives</span><span class="sxs-lookup"><span data-stu-id="0cd03-121">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="0cd03-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="0cd03-122">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="0cd03-123">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="0cd03-123">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="0cd03-124">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="0cd03-124">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
