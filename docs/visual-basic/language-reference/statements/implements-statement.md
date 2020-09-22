---
title: Implements, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873243"
---
# <a name="implements-statement"></a><span data-ttu-id="cc6d8-102">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="cc6d8-102">Implements Statement</span></span>

<span data-ttu-id="cc6d8-103">Spécifie une ou plusieurs interfaces, ou membres d’interface, qui doivent être implémentées dans la définition de la classe ou de la structure dans laquelle elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc6d8-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="cc6d8-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="cc6d8-105">Parts</span></span>  

 `interfacename`  
 <span data-ttu-id="cc6d8-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-106">Required.</span></span> <span data-ttu-id="cc6d8-107">Interface dont les propriétés, les procédures et les événements doivent être implémentés par les membres correspondants dans la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="cc6d8-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-108">Required.</span></span> <span data-ttu-id="cc6d8-109">Membre d’une interface qui est implémentée.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc6d8-110">Notes</span><span class="sxs-lookup"><span data-stu-id="cc6d8-110">Remarks</span></span>  

 <span data-ttu-id="cc6d8-111">Une interface est une collection de prototypes représentant les membres (propriétés, procédures et événements) encapsulés par l’interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="cc6d8-112">Les interfaces contiennent uniquement les déclarations pour les membres ; les classes et les structures implémentent ces membres.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="cc6d8-113">Pour plus d'informations, consultez [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d8-113">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="cc6d8-114">L' `Implements` instruction doit suivre immédiatement l' `Class` `Structure` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="cc6d8-115">Lorsque vous implémentez une interface, vous devez implémenter tous les membres déclarés dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="cc6d8-116">L’omission d’un membre est considérée comme une erreur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="cc6d8-117">Pour implémenter un membre individuel, vous spécifiez le mot clé [Implements](implements-clause.md) (qui est distinct de l' `Implements` instruction) lorsque vous déclarez le membre dans la classe ou la structure.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-117">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="cc6d8-118">Pour plus d'informations, consultez [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d8-118">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="cc6d8-119">Les classes peuvent utiliser des implémentations [privées](../modifiers/private.md) de propriétés et de procédures, mais ces membres sont accessibles uniquement en effectuant un cast d’une instance de la classe d’implémentation dans une variable déclarée comme étant du type de l’interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-119">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc6d8-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc6d8-120">Example</span></span>  

 <span data-ttu-id="cc6d8-121">L’exemple suivant montre comment utiliser l' `Implements` instruction pour implémenter des membres d’une interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="cc6d8-122">Il définit une interface nommée `ICustomerInfo` avec un événement, une propriété et une procédure.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="cc6d8-123">La classe `customerInfo` implémente tous les membres définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="cc6d8-124">Notez que la classe `customerInfo` utilise l' `Implements` instruction sur une ligne de code source distincte pour indiquer que la classe implémente tous les membres de l' `ICustomerInfo` interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="cc6d8-125">Ensuite, chaque membre de la classe utilise le `Implements` mot clé dans le cadre de sa déclaration de membre pour indiquer qu’il implémente ce membre d’interface.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc6d8-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc6d8-126">Example</span></span>  

 <span data-ttu-id="cc6d8-127">Les deux procédures suivantes montrent comment utiliser l’interface implémentée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="cc6d8-128">Pour tester l’implémentation, ajoutez ces procédures à votre projet et appelez la `testImplements` procédure.</span><span class="sxs-lookup"><span data-stu-id="cc6d8-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="cc6d8-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc6d8-129">See also</span></span>

- [<span data-ttu-id="cc6d8-130">Implémente</span><span class="sxs-lookup"><span data-stu-id="cc6d8-130">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="cc6d8-131">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="cc6d8-131">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="cc6d8-132">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cc6d8-132">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
