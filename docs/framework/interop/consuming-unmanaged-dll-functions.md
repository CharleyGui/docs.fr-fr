---
title: Consommation de fonctions DLL non managées
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399972"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="d54e1-102">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="d54e1-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="d54e1-103">L’appel de code non managé est un service qui permet au code managé d’appeler des fonctions non managées implémentées dans des bibliothèques de liens dynamiques (DLL), telles que celles de l’API Windows.</span><span class="sxs-lookup"><span data-stu-id="d54e1-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="d54e1-104">Il localise et appelle une fonction exportée, puis marshale ses arguments (entiers, chaînes, tableaux, structures, etc) au-delà des limites d’interopérabilité, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="d54e1-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="d54e1-105">Cette section présente les tâches liées à la consommation de fonctions DLL non managées et fournit plus d’informations sur l’appel de code non managé (PInvoke).</span><span class="sxs-lookup"><span data-stu-id="d54e1-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="d54e1-106">Outre les tâches suivantes, cette section comprend des remarques d'ordre général, ainsi qu'un lien vers des informations supplémentaires et des exemples.</span><span class="sxs-lookup"><span data-stu-id="d54e1-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="d54e1-107">Pour consommer des fonctions DLL exportées</span><span class="sxs-lookup"><span data-stu-id="d54e1-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="d54e1-108">[Identifiez les fonctions dans les DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="d54e1-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="d54e1-109">Vous devez au minimum spécifier le nom de la fonction et le nom de la DLL qui la contient.</span><span class="sxs-lookup"><span data-stu-id="d54e1-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="d54e1-110">[Créez une classe censée contenir des fonctions DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d54e1-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="d54e1-111">Vous pouvez utiliser une classe existante, créer une classe pour chaque fonction non managée ou bien créer une classe contenant un ensemble de fonctions non managées associées.</span><span class="sxs-lookup"><span data-stu-id="d54e1-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="d54e1-112">[Créez des prototypes dans du code managé](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="d54e1-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="d54e1-113">[Visual Basic] Utilisez l’instruction **Declare** avec les mots clés **Function** et **Lib**.</span><span class="sxs-lookup"><span data-stu-id="d54e1-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="d54e1-114">Dans certains cas rares, vous pouvez utiliser **DllImportAttribute** avec les mots clés **Shared Function**.</span><span class="sxs-lookup"><span data-stu-id="d54e1-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="d54e1-115">Ces cas sont expliqués plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="d54e1-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="d54e1-116">C# Utilisez **DllImportAttribute** pour identifier la dll et la fonction.</span><span class="sxs-lookup"><span data-stu-id="d54e1-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="d54e1-117">Marquez la méthode avec les modificateurs **static** et **extern**.</span><span class="sxs-lookup"><span data-stu-id="d54e1-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="d54e1-118">[C++] Utilisez **DllImportAttribute** pour identifier la DLL et la fonction.</span><span class="sxs-lookup"><span data-stu-id="d54e1-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="d54e1-119">Marquez la méthode ou la fonction wrapper avec **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="d54e1-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="d54e1-120">[Appelez une fonction DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="d54e1-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="d54e1-121">Appelez la méthode sur votre classe managée comme vous le feriez pour toute autre méthode managée.</span><span class="sxs-lookup"><span data-stu-id="d54e1-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="d54e1-122">Le [passage de structures](passing-structures.md) et l’[implémentation de fonctions de rappel](callback-functions.md) sont des cas spéciaux.</span><span class="sxs-lookup"><span data-stu-id="d54e1-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="d54e1-123">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="d54e1-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="d54e1-124">Présentation détaillée de l'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="d54e1-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="d54e1-125">L’appel de code non managé s’appuie sur les métadonnées pour localiser les fonctions exportées et marshaler leurs arguments au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d54e1-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="d54e1-126">L'illustration ci-dessous montre ce processus.</span><span class="sxs-lookup"><span data-stu-id="d54e1-126">The following illustration shows this process.</span></span>  
  
 ![Diagramme illustrant un appel de code non managé.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="d54e1-128">Quand un appel de code non managé appelle une fonction non managée, il exécute les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d54e1-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="d54e1-129">Il recherche la DLL contenant la fonction.</span><span class="sxs-lookup"><span data-stu-id="d54e1-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="d54e1-130">Il charge la DLL dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d54e1-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="d54e1-131">Il localise l'adresse de la fonction dans la mémoire et transmet ses arguments sur la pile, en marshalant les données selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="d54e1-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d54e1-132">La localisation et le chargement de la DLL, et la localisation de l'adresse de la fonction dans la mémoire, se produisent uniquement lors du premier appel à la fonction.</span><span class="sxs-lookup"><span data-stu-id="d54e1-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="d54e1-133">Il cède le contrôle à la fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="d54e1-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="d54e1-134">L'appel de code non managé lève des exceptions générées par la fonction non managée pour l'appelant managé.</span><span class="sxs-lookup"><span data-stu-id="d54e1-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54e1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d54e1-135">See also</span></span>

- [<span data-ttu-id="d54e1-136">Interopérabilité avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="d54e1-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="d54e1-137">Exemples d’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="d54e1-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="d54e1-138">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d54e1-138">Interop Marshaling</span></span>](interop-marshaling.md)
