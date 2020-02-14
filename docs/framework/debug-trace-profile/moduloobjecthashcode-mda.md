---
title: moduloObjectHashcode (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216184"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="c9226-102">moduloObjectHashcode (MDA)</span><span class="sxs-lookup"><span data-stu-id="c9226-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="c9226-103">L’Assistant Débogage managé `moduloObjectHashcode` modifie le comportement de la classe <xref:System.Object> pour effectuer une opération modulo sur le code de hachage retourné par la méthode <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9226-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c9226-104">Le modulo par défaut pour cet Assistant Débogage managé est 1, ce qui fait que <xref:System.Object.GetHashCode%2A> retourne 0 pour tous les objets.</span><span class="sxs-lookup"><span data-stu-id="c9226-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c9226-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c9226-105">Symptoms</span></span>  
 <span data-ttu-id="c9226-106">Après le passage à une nouvelle version du common language runtime, un programme ne s’exécute plus correctement :</span><span class="sxs-lookup"><span data-stu-id="c9226-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="c9226-107">Le programme reçoit un objet incorrect d’un <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="c9226-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="c9226-108">L’ordre d’énumération d’un <xref:System.Collections.Hashtable> a changé et le programme ne fonctionne plus correctement.</span><span class="sxs-lookup"><span data-stu-id="c9226-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="c9226-109">Deux objets qui étaient habituellement égaux ne le sont plus.</span><span class="sxs-lookup"><span data-stu-id="c9226-109">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="c9226-110">Deux objets qui étaient habituellement inégaux sont maintenant égaux.</span><span class="sxs-lookup"><span data-stu-id="c9226-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c9226-111">Cause :</span><span class="sxs-lookup"><span data-stu-id="c9226-111">Cause</span></span>  
 <span data-ttu-id="c9226-112">Votre programme reçoit peut-être un objet incorrect d’un <xref:System.Collections.Hashtable> en raison du fait que l’implémentation de la méthode <xref:System.Object.Equals%2A> sur la classe pour la clé dans le <xref:System.Collections.Hashtable> teste l’égalité des objets en comparant les résultats de l’appel à la méthode <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9226-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c9226-113">Les codes de hachage ne doivent pas être utilisés pour tester l’égalité entre des objets, car deux objets peuvent avoir le même code de hachage même si leurs champs respectifs ont des valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="c9226-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="c9226-114">Ces collisions de codes de hachage, bien que rares dans la pratique, se produisent.</span><span class="sxs-lookup"><span data-stu-id="c9226-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="c9226-115">L’effet de ceci sur une recherche dans <xref:System.Collections.Hashtable> est que deux clés qui ne sont pas égales apparaissent comme étant égales et que l’objet incorrect est retourné depuis le <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="c9226-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="c9226-116">Pour des raisons de performances, l’implémentation de <xref:System.Object.GetHashCode%2A> peut changer entre les versions du runtime : ainsi, des collisions qui ne se produisent pas sur une version peuvent se produire sur les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c9226-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="c9226-117">Activez cet Assistant Débogage managé pour tester si votre code comporte des bogues en cas de collision de codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="c9226-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="c9226-118">Quand il est activé, cet Assistant Débogage managé fait que la méthode <xref:System.Object.GetHashCode%2A> retourne 0, ce qui entraîne une collision de tous les codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="c9226-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="c9226-119">Le seul effet que l’activation de cet Assistant Débogage managé doit avoir sur votre programme est que celui-ci s’exécute plus lentement.</span><span class="sxs-lookup"><span data-stu-id="c9226-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="c9226-120">L’ordre d’énumération d’un <xref:System.Collections.Hashtable> peut changer d’une version du runtime à l’autre si l’algorithme utilisé pour calculer les codes de hachage de la clé change.</span><span class="sxs-lookup"><span data-stu-id="c9226-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="c9226-121">Pour tester si votre programme est dépendant de l’ordre d’énumération des clés ou des valeurs provenant d’une table de hachage, vous pouvez activer cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="c9226-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c9226-122">Résolution</span><span class="sxs-lookup"><span data-stu-id="c9226-122">Resolution</span></span>  
 <span data-ttu-id="c9226-123">N’utilisez jamais de codes de hachage en remplacement de l’identité d’un objet.</span><span class="sxs-lookup"><span data-stu-id="c9226-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="c9226-124">Implémentez le remplacement de la méthode <xref:System.Object.Equals%2A?displayProperty=nameWithType> de façon à ne pas comparer les codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="c9226-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="c9226-125">Ne créez pas de dépendances par rapport à l’ordre des énumérations de clés ou de valeurs dans des tables de hachage.</span><span class="sxs-lookup"><span data-stu-id="c9226-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c9226-126">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c9226-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="c9226-127">Les applications s’exécutent plus lentement quand cet Assistant Débogage managé est activé.</span><span class="sxs-lookup"><span data-stu-id="c9226-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="c9226-128">Cet Assistant Débogage managé prend le code de hachage qui aurait été retourné et retourne à la place le reste de la division par un modulo.</span><span class="sxs-lookup"><span data-stu-id="c9226-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c9226-129">Output</span><span class="sxs-lookup"><span data-stu-id="c9226-129">Output</span></span>  
 <span data-ttu-id="c9226-130">Cet Assistant Débogage managé n’a pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="c9226-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c9226-131">Configuration</span><span class="sxs-lookup"><span data-stu-id="c9226-131">Configuration</span></span>  
 <span data-ttu-id="c9226-132">L’attribut `modulus` spécifie le modulo utilisé sur le code de hachage.</span><span class="sxs-lookup"><span data-stu-id="c9226-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="c9226-133">La valeur par défaut est 1.</span><span class="sxs-lookup"><span data-stu-id="c9226-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9226-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9226-134">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c9226-135">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="c9226-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
