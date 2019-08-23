---
title: Implémentation de méthode dans les contrôles personnalisés
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931749"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="7d79b-102">Implémentation de méthode dans les contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="7d79b-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="7d79b-103">Une méthode est implémentée dans un contrôle comme dans tout autre composant.</span><span class="sxs-lookup"><span data-stu-id="7d79b-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="7d79b-104">En Visual Basic, si une méthode est nécessaire pour retourner une valeur, elle est implémentée en tant que `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="7d79b-105">Si aucune valeur n'est retournée, elle est implémentée en tant que `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="7d79b-106">Les méthodes sont déclarées à l'aide de la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="7d79b-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="7d79b-107">Les fonctions doivent spécifier un type de retour, tel qu'entier, chaîne, objet, etc., car elles retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="7d79b-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="7d79b-108">Le cas échéant, vous devez également spécifier les arguments acceptés par les procédures `Function` ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="7d79b-109">C# ne fait aucune différence entre les fonctions et les procédures, contrairement à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7d79b-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="7d79b-110">Une méthode retourne une valeur ou `void`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="7d79b-111">La syntaxe permettant de déclarer une méthode publique C# est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7d79b-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="7d79b-112">Quand vous déclarez une méthode, déclarez tous ses arguments en tant que types de données explicites, si possible.</span><span class="sxs-lookup"><span data-stu-id="7d79b-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="7d79b-113">Les arguments qui acceptent des références d'objet doivent être déclarés comme des types de classe spécifiques : par exemple, `As Widget` au lieu d'`As Object`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="7d79b-114">En Visual Basic, le paramètre `Option Strict` par défaut applique automatiquement cette règle.</span><span class="sxs-lookup"><span data-stu-id="7d79b-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="7d79b-115">Les arguments typés permettent au compilateur de détecter de nombreuses erreurs au cours du développement, plutôt qu'au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7d79b-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="7d79b-116">Le compilateur détecte systématiquement les erreurs, tandis que le test au moment de l'exécution est du même niveau qu'une suite de tests.</span><span class="sxs-lookup"><span data-stu-id="7d79b-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="7d79b-117">Méthodes surchargées</span><span class="sxs-lookup"><span data-stu-id="7d79b-117">Overloaded Methods</span></span>  
 <span data-ttu-id="7d79b-118">Si vous voulez permettre aux utilisateurs que vous contrôlez de fournir des combinaisons différentes de paramètres à une méthode, offrez plusieurs surcharges de la méthode, à l'aide de types de données explicites.</span><span class="sxs-lookup"><span data-stu-id="7d79b-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="7d79b-119">Évitez la création de paramètres déclarés `As Object` qui peuvent contenir tout type de données, car cela peut générer des erreurs qui ne seraient pas détectées pendant le test.</span><span class="sxs-lookup"><span data-stu-id="7d79b-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d79b-120">Le type de données universel du Common Language Runtime est `Object` plutôt que `Variant`.</span><span class="sxs-lookup"><span data-stu-id="7d79b-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="7d79b-121">`Variant` a été supprimé du langage.</span><span class="sxs-lookup"><span data-stu-id="7d79b-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="7d79b-122">Par exemple, la méthode `Spin` d'un hypothétique contrôle `Widget` peut permettre la spécification directe de la direction et de la vitesse de rotation, ou la spécification d'un autre objet `Widget` à partir duquel le moment cinétique doit être absorbé :</span><span class="sxs-lookup"><span data-stu-id="7d79b-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d79b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d79b-123">See also</span></span>

- [<span data-ttu-id="7d79b-124">Événements</span><span class="sxs-lookup"><span data-stu-id="7d79b-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="7d79b-125">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d79b-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
