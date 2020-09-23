---
title: Quand utiliser une énumération
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 7b1b269a5d28d89cd491bac88fbefd4547fdc3c3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095627"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="03d56-102">Quand utiliser une énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03d56-102">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="03d56-103">Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées.</span><span class="sxs-lookup"><span data-stu-id="03d56-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="03d56-104">Une énumération, ou `Enum` , est un nom symbolique pour un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="03d56-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="03d56-105">Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des ensembles de constantes à utiliser avec des variables et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="03d56-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="03d56-106">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="03d56-106">When to Use an Enumeration</span></span>  

 <span data-ttu-id="03d56-107">Chaque fois qu’une procédure accepte un ensemble limité de variables, envisagez d’utiliser une énumération.</span><span class="sxs-lookup"><span data-stu-id="03d56-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="03d56-108">Les énumérations rendent le code plus clair et plus lisible, en particulier quand des noms explicites sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="03d56-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="03d56-109">Les avantages de l’utilisation des énumérations sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="03d56-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="03d56-110">Réduit les erreurs dues à la transposition ou à la frappe de nombres.</span><span class="sxs-lookup"><span data-stu-id="03d56-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="03d56-111">Facilite la modification des valeurs à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="03d56-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="03d56-112">Rend le code plus facile à lire, ce qui signifie qu’il est moins probable que des erreurs se produiront.</span><span class="sxs-lookup"><span data-stu-id="03d56-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="03d56-113">Garantit la compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="03d56-113">Ensures forward compatibility.</span></span> <span data-ttu-id="03d56-114">Avec les énumérations, votre code risque d’échouer si, à l’avenir, un utilisateur modifie les valeurs correspondant aux noms des membres.</span><span class="sxs-lookup"><span data-stu-id="03d56-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="03d56-115">Énumération des noms</span><span class="sxs-lookup"><span data-stu-id="03d56-115">Naming Enumerations</span></span>  

 <span data-ttu-id="03d56-116">Utilisez une convention d’affectation de noms pour les membres de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="03d56-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="03d56-117">Lorsque Visual Basic rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencées contiennent le même nom.</span><span class="sxs-lookup"><span data-stu-id="03d56-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="03d56-118">Utilisez un préfixe unique qui identifie les valeurs de votre application ou composant.</span><span class="sxs-lookup"><span data-stu-id="03d56-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="03d56-119">Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération ou utiliser l' `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="03d56-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="03d56-120">Pour plus d’informations, consultez [énumérations et qualification de nom](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="03d56-120">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="03d56-121">Énumérations prédéfinies</span><span class="sxs-lookup"><span data-stu-id="03d56-121">Predefined Enumerations</span></span>  

 <span data-ttu-id="03d56-122">Visual Basic fournit un certain nombre d’énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult` , pour faciliter votre code.</span><span class="sxs-lookup"><span data-stu-id="03d56-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="03d56-123">Pour obtenir la liste de ces [énumérations, consultez constantes et énumérations](../../../language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="03d56-123">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d56-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03d56-124">See also</span></span>

- [<span data-ttu-id="03d56-125">How to: Declare an, énumération</span><span class="sxs-lookup"><span data-stu-id="03d56-125">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="03d56-126">Comment : faire référence à un membre d'énumération</span><span class="sxs-lookup"><span data-stu-id="03d56-126">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="03d56-127">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="03d56-127">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="03d56-128">Comment : itérer au sein d'une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03d56-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="03d56-129">Comment : déterminer la chaîne associée à une valeur d'énumération</span><span class="sxs-lookup"><span data-stu-id="03d56-129">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="03d56-130">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="03d56-130">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="03d56-131">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="03d56-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
