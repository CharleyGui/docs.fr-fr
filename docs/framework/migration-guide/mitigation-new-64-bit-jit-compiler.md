---
title: 'Atténuation : Nouveau compilateur JIT 64 bits'
description: Découvrez le nouveau compilateur JIT 64 bits inclus dans .NET Framework 4,6 et un comportement inattendu ou des exceptions qui peuvent se produire pendant la compilation.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 228c286f6c5620dc838df5002edc60863a0fe4e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256597"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="20f1b-103">Atténuation : Nouveau compilateur JIT 64 bits</span><span class="sxs-lookup"><span data-stu-id="20f1b-103">Mitigation: New 64-bit JIT Compiler</span></span>

<span data-ttu-id="20f1b-104">À compter de .NET Framework 4,6, le runtime comprend un nouveau compilateur JIT 64 bits pour la compilation juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="20f1b-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="20f1b-105">Cette modification n’affecte pas la compilation avec le compilateur JIT 32 bits.</span><span class="sxs-lookup"><span data-stu-id="20f1b-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="20f1b-106">Comportement inattendu ou exceptions</span><span class="sxs-lookup"><span data-stu-id="20f1b-106">Unexpected behavior or exceptions</span></span>  

 <span data-ttu-id="20f1b-107">Dans certains cas, la compilation avec le nouveau compilateur JIT 64 bits entraîne une exception de runtime ou le non-respect du comportement lors de l’exécution de code compilé par l’ancien compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="20f1b-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="20f1b-108">Voici quelques-unes des différences connues :</span><span class="sxs-lookup"><span data-stu-id="20f1b-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20f1b-109">Tous ces problèmes connus ont été résolus dans le nouveau compilateur 64 bits fourni avec le SDK .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="20f1b-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="20f1b-110">La plupart ont également été résolus dans les versions de maintenance du .NET Framework 4.6 et 4.6.1, qui sont disponibles via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="20f1b-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="20f1b-111">Vous pouvez éviter ces problèmes en vous assurant que votre version de Windows est à jour, ou en mettant à niveau vers .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="20f1b-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="20f1b-112">Dans certaines conditions, une opération d’unboxing peut lever une <xref:System.NullReferenceException> dans les versions Release avec l’optimisation activée.</span><span class="sxs-lookup"><span data-stu-id="20f1b-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="20f1b-113">Dans certains cas, l’exécution du code de production dans un corps de méthode volumineux peut lever une <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="20f1b-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="20f1b-114">Dans certaines conditions, les structures passées à une méthode sont traitées comme des types référence plutôt que des types valeur dans les versions Release.</span><span class="sxs-lookup"><span data-stu-id="20f1b-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="20f1b-115">Ce problème se manifeste notamment lorsque des éléments dans une collection apparaissent dans un ordre inattendu.</span><span class="sxs-lookup"><span data-stu-id="20f1b-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="20f1b-116">Dans certaines conditions, la comparaison de valeurs <xref:System.UInt16> avec le bit le plus élevé est incorrecte si l’optimisation est activée.</span><span class="sxs-lookup"><span data-stu-id="20f1b-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="20f1b-117">Sous certaines conditions, en particulier lors de l’initialisation de tableaux de valeurs, l’initialisation de la mémoire par l’instruction <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> du langage intermédiaire peut initialiser la mémoire avec une valeur incorrecte.</span><span class="sxs-lookup"><span data-stu-id="20f1b-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="20f1b-118">Cela peut entraîner une exception non gérée ou une sortie incorrecte.</span><span class="sxs-lookup"><span data-stu-id="20f1b-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="20f1b-119">Dans certains cas rares, un test conditionnel binaire peut retourner une valeur <xref:System.Boolean> incorrecte ou lever une exception si les optimisations du compilateur sont activées.</span><span class="sxs-lookup"><span data-stu-id="20f1b-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="20f1b-120">Sous certaines conditions, si une instruction `if` est utilisée pour tester une condition avant d’entrer dans un bloc `try` et dans la sortie du bloc `try`, et que la même condition est évaluée dans le bloc `catch` ou `finally`, le nouveau compilateur JIT 64 bits supprime la condition `if` du bloc `catch` ou `finally` lorsqu’il optimise le code.</span><span class="sxs-lookup"><span data-stu-id="20f1b-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="20f1b-121">Par conséquent, le code à l’intérieur de l’instruction `if` dans le bloc `catch` ou `finally` est exécuté de manière non conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="20f1b-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>

## <a name="mitigation-of-known-issues"></a><span data-ttu-id="20f1b-122">Atténuation des problèmes connus</span><span class="sxs-lookup"><span data-stu-id="20f1b-122">Mitigation of known issues</span></span>  

 <span data-ttu-id="20f1b-123">Si vous rencontrez les problèmes répertoriés ci-dessus, vous pouvez les traiter en procédant d’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="20f1b-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="20f1b-124">Mettez à niveau vers .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="20f1b-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="20f1b-125">Le nouveau compilateur 64 bits inclus avec .NET Framework 4.6.2 résout chacun de ces problèmes connus.</span><span class="sxs-lookup"><span data-stu-id="20f1b-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="20f1b-126">Assurez-vous que votre version de Windows est à jour en exécutant Windows Update.</span><span class="sxs-lookup"><span data-stu-id="20f1b-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="20f1b-127">Les mises à jour de service pour .NET Framework 4.6 et 4.6.1 corrigent chacun de ces problèmes, à l’exception de <xref:System.NullReferenceException> dans une opération d’unboxing.</span><span class="sxs-lookup"><span data-stu-id="20f1b-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="20f1b-128">Compilez avec l’ancien compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="20f1b-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="20f1b-129">Consultez la section [Atténuation des autres problèmes](#Other) pour plus d’informations sur cette procédure.</span><span class="sxs-lookup"><span data-stu-id="20f1b-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>

## <a name="mitigation-of-other-issues"></a><span data-ttu-id="20f1b-130">Atténuation des autres problèmes</span><span class="sxs-lookup"><span data-stu-id="20f1b-130">Mitigation of other issues</span></span>  

 <span data-ttu-id="20f1b-131">Si vous rencontrez une autre différence de comportement entre le code compilé avec l’ancien compilateur JIT 64 bits et celui compilé avec le nouveau compilateur, ou entre les versions Debug et Release de votre application lorsque les deux sont compilées avec le nouveau compilateur JIT 64 bits, vous pouvez procéder comme suit pour compiler votre application avec l’ancien compilateur JIT 64 bits :</span><span class="sxs-lookup"><span data-stu-id="20f1b-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="20f1b-132">Pour chaque application, vous pouvez ajouter l' [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) élément au fichier de configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="20f1b-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="20f1b-133">Ce qui suit désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise l’ancien compilateur à la place.</span><span class="sxs-lookup"><span data-stu-id="20f1b-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="20f1b-134">Pour chaque utilisateur concerné, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`.</span><span class="sxs-lookup"><span data-stu-id="20f1b-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="20f1b-135">La valeur 1 active l’ancien compilateur JIT 64 bits ; la valeur 0 le désactive et active le nouveau compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="20f1b-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="20f1b-136">Pour chaque machine concernée, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`.</span><span class="sxs-lookup"><span data-stu-id="20f1b-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="20f1b-137">La valeur 1 active l’ancien compilateur JIT 64 bits ; la valeur 0 le désactive et active le nouveau compilateur JIT 64 bits.</span><span class="sxs-lookup"><span data-stu-id="20f1b-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="20f1b-138">Vous pouvez également nous indiquer votre problème en signalant un bogue sur [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="20f1b-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f1b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20f1b-139">See also</span></span>

- [<span data-ttu-id="20f1b-140">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="20f1b-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="20f1b-141">\<useLegacyJit> Appartient</span><span class="sxs-lookup"><span data-stu-id="20f1b-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
