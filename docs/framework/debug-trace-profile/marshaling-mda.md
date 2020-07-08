---
title: Assistant Débogage managé marshaling
description: Passez en revue l’Assistant Débogage managé (MDA) de marshaling, qui est appelé si le CLR définit des informations de marshaling pour un paramètre de méthode ou un champ de structure.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: 77811c526d1770b91b14aa1199dfc7b3177e6c59
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051153"
---
# <a name="marshaling-mda"></a><span data-ttu-id="5c2ad-103">Assistant Débogage managé marshaling</span><span class="sxs-lookup"><span data-stu-id="5c2ad-103">marshaling MDA</span></span>
<span data-ttu-id="5c2ad-104">L'Assistant Débogage managé (MDA) `marshaling` est activé quand le CLR définit des informations de marshaling pour un paramètre de méthode ou un champ de structure.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="5c2ad-105">Ce MDA ne fonctionne pas pour les assemblys compilés juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="5c2ad-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5c2ad-106">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="5c2ad-106">Effect on the Runtime</span></span>  
 <span data-ttu-id="5c2ad-107">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5c2ad-108">Sortie</span><span class="sxs-lookup"><span data-stu-id="5c2ad-108">Output</span></span>  
 <span data-ttu-id="5c2ad-109">Le MDA affiche le type du paramètre ou du champ dans les contextes managés et non managés ainsi que la structure ou la méthode qui contient ce type.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="5c2ad-110">Voici un exemple de sortie pour un champ :</span><span class="sxs-lookup"><span data-stu-id="5c2ad-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="5c2ad-111">Configuration</span><span class="sxs-lookup"><span data-stu-id="5c2ad-111">Configuration</span></span>  
 <span data-ttu-id="5c2ad-112">La configuration du MDA vous permet de filtrer les informations de marshaling signalées en fonction des noms de champs ou de méthodes impliqués.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="5c2ad-113">L'exemple suivant illustre l'utilisation des éléments `methodFilter`, `fieldFilter` et `match` pour spécifier des filtres.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="5c2ad-114">L’affectation d' `name` un astérisque () à l’attribut \* correspond à tout.</span><span class="sxs-lookup"><span data-stu-id="5c2ad-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c2ad-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c2ad-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5c2ad-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="5c2ad-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5c2ad-117">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5c2ad-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
