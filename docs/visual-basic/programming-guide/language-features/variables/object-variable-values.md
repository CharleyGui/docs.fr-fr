---
title: Valeurs des variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 1dd3e8cd68086fe116daf0678a1a19881f1ae9c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410346"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="d498e-102">Valeurs des variables objets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d498e-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="d498e-103">Une variable du [type de données Object](../../../language-reference/data-types/object-data-type.md) peut faire référence à des données de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="d498e-103">A variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="d498e-104">La valeur que vous stockez dans une `Object` variable est conservée ailleurs en mémoire, tandis que la variable elle-même contient un pointeur vers les données.</span><span class="sxs-lookup"><span data-stu-id="d498e-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="d498e-105">Fonctions du classifieur d’objets</span><span class="sxs-lookup"><span data-stu-id="d498e-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="d498e-106">Visual Basic fournit des fonctions qui retournent des informations sur `Object` la référence à une variable, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d498e-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d498e-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="d498e-107">Function</span></span>|<span data-ttu-id="d498e-108">Retourne la valeur true si la variable objet fait référence à</span><span class="sxs-lookup"><span data-stu-id="d498e-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="d498e-109">Tableau de valeurs, plutôt qu’une valeur unique</span><span class="sxs-lookup"><span data-stu-id="d498e-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="d498e-110">Une valeur de [type de données date](../../../language-reference/data-types/date-data-type.md) , ou une chaîne qui peut être interprétée comme une valeur de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="d498e-110">A [Date Data Type](../../../language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="d498e-111">Objet de type <xref:System.DBNull> , qui représente des données manquantes ou inexistantes.</span><span class="sxs-lookup"><span data-stu-id="d498e-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="d498e-112">Objet d’exception, qui dérive de<xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="d498e-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="d498e-113">[Rien](../../../language-reference/nothing.md), autrement dit, aucun objet n’est actuellement assigné à la variable</span><span class="sxs-lookup"><span data-stu-id="d498e-113">[Nothing](../../../language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="d498e-114">Un nombre, ou une chaîne qui peut être interprétée comme un nombre</span><span class="sxs-lookup"><span data-stu-id="d498e-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="d498e-115">Type référence (par exemple, une chaîne, un tableau, un délégué ou un type de classe)</span><span class="sxs-lookup"><span data-stu-id="d498e-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="d498e-116">Vous pouvez utiliser ces fonctions pour éviter d’envoyer une valeur non valide à une opération ou à une procédure.</span><span class="sxs-lookup"><span data-stu-id="d498e-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="d498e-117">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="d498e-117">TypeOf Operator</span></span>  
 <span data-ttu-id="d498e-118">Vous pouvez également utiliser l' [opérateur typeof](../../../language-reference/operators/typeof-operator.md) pour déterminer si une variable objet fait actuellement référence à un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="d498e-118">You can also use the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="d498e-119">L' `TypeOf` expression... `Is` prend la valeur `True` si le type au moment de l’exécution de l’opérande est dérivé de ou implémente le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d498e-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="d498e-120">L’exemple suivant utilise `TypeOf` sur les variables objets qui font référence aux types valeur et référence.</span><span class="sxs-lookup"><span data-stu-id="d498e-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="d498e-121">L’exemple précédent écrit les lignes suivantes dans la fenêtre de **débogage** :</span><span class="sxs-lookup"><span data-stu-id="d498e-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="d498e-122">La variable objet `num` fait référence à des données de type `Integer` et `frm` fait référence à un objet de classe <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="d498e-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="d498e-123">Tableaux d’objets</span><span class="sxs-lookup"><span data-stu-id="d498e-123">Object Arrays</span></span>  
 <span data-ttu-id="d498e-124">Vous pouvez déclarer et utiliser un tableau de `Object` variables.</span><span class="sxs-lookup"><span data-stu-id="d498e-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="d498e-125">Cela est utile lorsque vous devez gérer une variété de types de données et de classes d’objets.</span><span class="sxs-lookup"><span data-stu-id="d498e-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="d498e-126">Tous les éléments d’un tableau doivent avoir le même type de données déclaré.</span><span class="sxs-lookup"><span data-stu-id="d498e-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="d498e-127">La déclaration de ce type de données `Object` vous permet de stocker des objets et des instances de classe avec d’autres types de données dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="d498e-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d498e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d498e-128">See also</span></span>

- [<span data-ttu-id="d498e-129">Variables objets</span><span class="sxs-lookup"><span data-stu-id="d498e-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="d498e-130">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="d498e-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="d498e-131">Affectation des variables objets</span><span class="sxs-lookup"><span data-stu-id="d498e-131">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="d498e-132">Comment : référencer l'instance actuelle d'un objet</span><span class="sxs-lookup"><span data-stu-id="d498e-132">How to: Refer to the Current Instance of an Object</span></span>](how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="d498e-133">Comment : déterminer le type désigné par une variable objet</span><span class="sxs-lookup"><span data-stu-id="d498e-133">How to: Determine What Type an Object Variable Refers To</span></span>](how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="d498e-134">Comment : déterminer si deux objets sont liés</span><span class="sxs-lookup"><span data-stu-id="d498e-134">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="d498e-135">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="d498e-135">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="d498e-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="d498e-136">Data Types</span></span>](../data-types/index.md)
