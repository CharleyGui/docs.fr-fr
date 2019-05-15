---
title: 'Procédure : raccorder un délégué à l’aide de la réflexion'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bc4b4df6829f5b86dff400c5cd7cbd3d86f5507
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591532"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="931ed-102">Procédure : raccorder un délégué à l’aide de la réflexion</span><span class="sxs-lookup"><span data-stu-id="931ed-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="931ed-103">Quand vous utilisez la réflexion pour charger et exécuter des assemblys, vous ne pouvez pas utiliser des fonctionnalités de langage telles que l’opérateur C# `+=` ou l’[instruction Visual Basic AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) pour raccorder des événements.</span><span class="sxs-lookup"><span data-stu-id="931ed-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="931ed-104">Les procédures suivantes montrent comment raccorder une méthode existante à un événement en obtenant tous les types nécessaires par réflexion, et comment créer une méthode dynamique à l’aide de l’émission de réflexion et la raccorder à un événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="931ed-105">Pour découvrir une autre manière de raccorder un délégué de gestion des événements, consultez l’exemple de code relatif à la méthode <xref:System.Reflection.EventInfo.AddEventHandler%2A> de la classe <xref:System.Reflection.EventInfo>.</span><span class="sxs-lookup"><span data-stu-id="931ed-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="931ed-106">Pour raccorder un délégué à l’aide de la réflexion</span><span class="sxs-lookup"><span data-stu-id="931ed-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="931ed-107">Chargez un assembly qui contient un type qui déclenche des événements.</span><span class="sxs-lookup"><span data-stu-id="931ed-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="931ed-108">Les assemblys sont habituellement chargés avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="931ed-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="931ed-109">Pour simplifier cet exemple, un formulaire dérivé dans l’assembly actuel est utilisé. La méthode <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> est donc utilisée pour charger l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="931ed-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="931ed-110">Obtenez un objet <xref:System.Type> représentant le type et créez une instance du type.</span><span class="sxs-lookup"><span data-stu-id="931ed-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="931ed-111">La méthode <xref:System.Activator.CreateInstance%28System.Type%29> est utilisée dans le code suivant car le formulaire a un constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="931ed-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="931ed-112">Vous pouvez utiliser plusieurs autres surcharges de la méthode <xref:System.Activator.CreateInstance%2A> si le type que vous créez n’a pas de constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="931ed-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="931ed-113">La nouvelle instance est stockée en tant que type <xref:System.Object> pour conserver l’illusion que l’assembly est inconnu.</span><span class="sxs-lookup"><span data-stu-id="931ed-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="931ed-114">(La réflexion vous autorise à obtenir les types dans un assembly sans connaître leurs noms à l’avance.)</span><span class="sxs-lookup"><span data-stu-id="931ed-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="931ed-115">Obtenez un objet <xref:System.Reflection.EventInfo> représentant l’événement, et utilisez la propriété <xref:System.Reflection.EventInfo.EventHandlerType%2A> pour obtenir le type de délégué utilisé pour gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="931ed-116">Dans le code suivant, un <xref:System.Reflection.EventInfo> pour l’événement <xref:System.Windows.Forms.Control.Click> est obtenu.</span><span class="sxs-lookup"><span data-stu-id="931ed-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="931ed-117">Obtenez un objet <xref:System.Reflection.MethodInfo> représentant la méthode qui gère l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="931ed-118">Le code complet du programme dans la section Exemple plus loin dans cette rubrique contient une méthode qui correspond à la signature du délégué <xref:System.EventHandler>, qui gère l’événement <xref:System.Windows.Forms.Control.Click>, mais vous pouvez également générer des méthodes dynamiques au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="931ed-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="931ed-119">Pour plus d’informations, consultez la procédure associée expliquant comment générer un gestionnaire d’événements au moment de l’exécution à l’aide d’une méthode dynamique.</span><span class="sxs-lookup"><span data-stu-id="931ed-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="931ed-120">Créez une instance du délégué à l’aide de la méthode <xref:System.Delegate.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="931ed-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="931ed-121">Cette méthode étant statique (`Shared` en Visual Basic), vous devez fournir le type délégué.</span><span class="sxs-lookup"><span data-stu-id="931ed-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="931ed-122">Nous vous recommandons d’utiliser les surcharges de <xref:System.Delegate.CreateDelegate%2A> qui prennent un <xref:System.Reflection.MethodInfo>.</span><span class="sxs-lookup"><span data-stu-id="931ed-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="931ed-123">Obtenez la méthode d’accesseur `add` et appelez-la pour raccorder l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="931ed-124">Tous les événements ont un accesseur `add` et un accesseur `remove`, qui sont masqués par la syntaxe des langages de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="931ed-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="931ed-125">Par exemple, C# utilise l’opérateur `+=` pour raccorder des événements, et Visual Basic utilise l’[instruction AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="931ed-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="931ed-126">Le code suivant obtient l’accesseur `add` de l’événement <xref:System.Windows.Forms.Control.Click> et l’appelle avec liaison tardive, en passant l’instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="931ed-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="931ed-127">Les arguments doivent être passés sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="931ed-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="931ed-128">Testez l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-128">Test the event.</span></span> <span data-ttu-id="931ed-129">Le code suivant montre le formulaire défini dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="931ed-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="931ed-130">Quand vous cliquez sur le formulaire, le gestionnaire d’événements est appelé.</span><span class="sxs-lookup"><span data-stu-id="931ed-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="931ed-131">Pour générer un gestionnaire d’événements au moment de l’exécution à l’aide d’une méthode dynamique</span><span class="sxs-lookup"><span data-stu-id="931ed-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="931ed-132">Vous pouvez générer des méthodes de gestionnaire d’événements au moment de l’exécution, à l’aide de méthodes dynamiques légères et de l’émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="931ed-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="931ed-133">Pour créer un gestionnaire d’événements, vous avez besoin du type de retour et des types de paramètres du délégué.</span><span class="sxs-lookup"><span data-stu-id="931ed-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="931ed-134">Vous pouvez les obtenir en examinant la méthode `Invoke` du délégué.</span><span class="sxs-lookup"><span data-stu-id="931ed-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="931ed-135">Le code suivant utilise les méthodes `GetDelegateReturnType` et `GetDelegateParameterTypes` pour obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="931ed-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="931ed-136">Vous trouverez le code de ces méthodes dans la section Exemple plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="931ed-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="931ed-137">Comme il n’est pas nécessaire de nommer un <xref:System.Reflection.Emit.DynamicMethod>, la chaîne vide peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="931ed-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="931ed-138">Dans le code suivant, le dernier argument associe la méthode dynamique au type actuel, ce qui donne au délégué accès à tous les membres privés et publics de la classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="931ed-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="931ed-139">Générez un corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="931ed-139">Generate a method body.</span></span> <span data-ttu-id="931ed-140">Cette méthode charge une chaîne, appelle la surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> qui prend une chaîne, dépile la valeur de retour (puisque le gestionnaire n’a aucun type de retour) et retourne.</span><span class="sxs-lookup"><span data-stu-id="931ed-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="931ed-141">Pour en savoir plus sur l’émission de méthodes dynamiques, consultez [Guide pratique pour définir et exécuter des méthodes dynamiques](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="931ed-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="931ed-142">Terminez l’exécution de la méthode dynamique en appelant sa méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="931ed-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="931ed-143">Utilisez l’accesseur `add` pour ajouter le délégué à la liste d’appels de l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="931ed-144">Testez l’événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-144">Test the event.</span></span> <span data-ttu-id="931ed-145">Le code suivant charge le formulaire défini dans l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="931ed-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="931ed-146">Quand vous cliquez sur le formulaire, le gestionnaire d’événements prédéfini et le gestionnaire d’événements émis sont appelés.</span><span class="sxs-lookup"><span data-stu-id="931ed-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="931ed-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="931ed-147">Example</span></span>  
 <span data-ttu-id="931ed-148">L’exemple de code suivant montre comment raccorder une méthode existante à un événement à l’aide de la réflexion, et également comment utiliser la classe <xref:System.Reflection.Emit.DynamicMethod> pour émettre une méthode au moment de l’exécution et la raccorder à un événement.</span><span class="sxs-lookup"><span data-stu-id="931ed-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="931ed-149">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="931ed-149">Compiling the Code</span></span>  
  
- <span data-ttu-id="931ed-150">Le code contient les instructions `using` C# (`Imports` en Visual Basic) nécessaires à la compilation.</span><span class="sxs-lookup"><span data-stu-id="931ed-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
- <span data-ttu-id="931ed-151">Aucune référence d’assembly supplémentaire n’est nécessaire pour la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="931ed-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="931ed-152">Dans Visual Studio, vous devez ajouter une référence à System.Windows.Forms.dll car cet exemple est une application console.</span><span class="sxs-lookup"><span data-stu-id="931ed-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
- <span data-ttu-id="931ed-153">Compilez le code sur la ligne de commande à l’aide de csc.exe, vbc.exe ou cl.exe.</span><span class="sxs-lookup"><span data-stu-id="931ed-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="931ed-154">Pour compiler le code dans Visual Studio, placez-le dans un modèle de projet d’application console.</span><span class="sxs-lookup"><span data-stu-id="931ed-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931ed-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="931ed-155">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="931ed-156">Guide pratique pour définir et exécuter des méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="931ed-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="931ed-157">Réflexion</span><span class="sxs-lookup"><span data-stu-id="931ed-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
