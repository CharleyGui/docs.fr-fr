---
title: Migration de votre application du Windows Store vers .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 987669fc51eeaf7e3bdef3e91a2f1ce23164a055
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81389700"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="95a8c-102">Migrer votre application du Windows Store vers .NET Native</span><span class="sxs-lookup"><span data-stu-id="95a8c-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="95a8c-103">.NET Native fournit une compilation statique des applications dans le Windows Store ou sur l’ordinateur du développeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="95a8c-104">Cela diffère de la compilation dynamique effectuée pour les applications du Windows Store par le compilateur juste-à-temps (JIT) ou le [générateur d'images natives (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) sur l'appareil.</span><span class="sxs-lookup"><span data-stu-id="95a8c-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="95a8c-105">Malgré les différences, .NET Native tente de maintenir la compatibilité avec [.net pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="95a8c-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="95a8c-106">Pour l’essentiel, les éléments qui fonctionnent sur .NET pour les applications du Windows Store fonctionnent également avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="95a8c-107">Toutefois, dans certains cas, vous pouvez rencontrer des changements de comportement.</span><span class="sxs-lookup"><span data-stu-id="95a8c-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="95a8c-108">Ce document traite de ces différences entre le .NET standard pour les applications du Windows Store et .NET Native dans les domaines suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="95a8c-109">Différences générales au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="95a8c-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="95a8c-110">Différences de programmation dynamique</span><span class="sxs-lookup"><span data-stu-id="95a8c-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="95a8c-111">Autres différences en matière de réflexion</span><span class="sxs-lookup"><span data-stu-id="95a8c-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="95a8c-112">API et scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="95a8c-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="95a8c-113">Différences concernant Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95a8c-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="95a8c-114">Différences générales au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="95a8c-114">General runtime differences</span></span>

- <span data-ttu-id="95a8c-115">Les exceptions, telles que <xref:System.TypeLoadException> , qui sont levées par le compilateur JIT quand une application s’exécute sur le Common Language Runtime (CLR) entraînent généralement des erreurs au moment de la compilation lorsqu’elles sont traitées par .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="95a8c-116">N'appelez pas la méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> à partir du thread d'interface utilisateur d'une application.</span><span class="sxs-lookup"><span data-stu-id="95a8c-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="95a8c-117">Cela peut entraîner un blocage sur .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="95a8c-118">Ne vous fiez pas à l'ordre d'appel des constructeurs de classe statique.</span><span class="sxs-lookup"><span data-stu-id="95a8c-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="95a8c-119">Dans .NET Native, l’ordre d’appel est différent de l’ordre sur le runtime standard.</span><span class="sxs-lookup"><span data-stu-id="95a8c-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="95a8c-120">(Même avec le runtime standard, évitez de vous fier à l'ordre d'exécution des constructeurs de classe statique.)</span><span class="sxs-lookup"><span data-stu-id="95a8c-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="95a8c-121">Des boucles infinies sans appel (par exemple, `while(true);`) sur n'importe quel thread peuvent entraîner l'arrêt de l'application.</span><span class="sxs-lookup"><span data-stu-id="95a8c-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="95a8c-122">Il en va de même dans le cas des attentes de longues durées ou infinies.</span><span class="sxs-lookup"><span data-stu-id="95a8c-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="95a8c-123">Certains cycles d’initialisation générique ne lèvent pas d’exceptions dans .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="95a8c-124">Par exemple, le code suivant lève une exception <xref:System.TypeLoadException> sur le CLR standard,</span><span class="sxs-lookup"><span data-stu-id="95a8c-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="95a8c-125">Dans .NET Native, cela ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="95a8c-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="95a8c-126">Dans certains cas, .NET Native fournit différentes implémentations de .NET Framework bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="95a8c-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="95a8c-127">Un objet retourné par une méthode implémente toujours les membres du type retourné.</span><span class="sxs-lookup"><span data-stu-id="95a8c-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="95a8c-128">Toutefois, l'implémentation de sa sauvegarde étant différente, vous ne pourrez peut-être pas effectuer un cast vers le même ensemble de types comme vous le pourriez sur d'autres plateformes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95a8c-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="95a8c-129">Par exemple, dans certains cas, vous ne pourrez peut-être pas effectuer un cast de l'objet d'interface <xref:System.Collections.Generic.IEnumerable%601> retourné par des méthodes telles que <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> vers `T[]`.</span><span class="sxs-lookup"><span data-stu-id="95a8c-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="95a8c-130">Le cache WinInet n’est pas activé par défaut sur .NET pour les applications du Windows Store, mais il se trouve sur .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="95a8c-131">Cela améliore les performances, mais a des implications pour les jeux de travail.</span><span class="sxs-lookup"><span data-stu-id="95a8c-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="95a8c-132">Aucune action n'est nécessaire de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="95a8c-133">Différences de programmation dynamique</span><span class="sxs-lookup"><span data-stu-id="95a8c-133">Dynamic programming differences</span></span>

<span data-ttu-id="95a8c-134">.NET Native des liens statiques dans le code à partir du .NET Framework pour que l’application de code soit locale pour des performances maximales.</span><span class="sxs-lookup"><span data-stu-id="95a8c-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="95a8c-135">Cependant, la taille des binaires doit demeurer petite, pour que l'ensemble du .NET Framework ne soit pas sollicité.</span><span class="sxs-lookup"><span data-stu-id="95a8c-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="95a8c-136">Le compilateur .NET Native résout cette limitation en utilisant un réducteur de dépendances qui supprime les références au code inutilisé.</span><span class="sxs-lookup"><span data-stu-id="95a8c-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="95a8c-137">Toutefois, .NET Native peut ne pas conserver ou générer des informations de type et du code quand ces informations ne peuvent pas être déduites statiquement au moment de la compilation, mais qu’elles sont récupérées dynamiquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="95a8c-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="95a8c-138">.NET Native active la réflexion et la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="95a8c-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="95a8c-139">Toutefois, tous les types ne peuvent pas être marqués pour réflexion, car la taille du code généré serait alors trop grande (notamment car la réflexion d'API publiques dans le .NET Framework est prise en charge).</span><span class="sxs-lookup"><span data-stu-id="95a8c-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="95a8c-140">Le compilateur .NET Native permet de choisir intelligemment les types devant prendre en charge la réflexion, et il conserve les métadonnées et génère le code uniquement pour ces types.</span><span class="sxs-lookup"><span data-stu-id="95a8c-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="95a8c-141">Par exemple, pour la liaison de données, une application doit pouvoir mapper les noms de propriété sur les fonctions.</span><span class="sxs-lookup"><span data-stu-id="95a8c-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="95a8c-142">Dans .NET pour les applications du Windows Store, le Common Language Runtime utilise automatiquement la réflexion pour fournir cette fonctionnalité pour les types managés et les types natifs disponibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="95a8c-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="95a8c-143">Dans .NET Native, le compilateur comprend automatiquement les métadonnées des types auxquels vous liez des données.</span><span class="sxs-lookup"><span data-stu-id="95a8c-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="95a8c-144">Le compilateur .NET Native peut également gérer les types génériques couramment utilisés tels que <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602> , qui fonctionnent sans nécessiter d’indicateurs ou de directives.</span><span class="sxs-lookup"><span data-stu-id="95a8c-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="95a8c-145">Le mot clé [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) est également pris en charge, dans certaines limites.</span><span class="sxs-lookup"><span data-stu-id="95a8c-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="95a8c-146">Vous devez tester minutieusement tous les chemins de code dynamiques quand vous portez votre application sur .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="95a8c-147">La configuration par défaut de .NET Native est suffisante pour la plupart des développeurs, mais certains développeurs peuvent souhaiter ajuster leurs configurations à l’aide d’un fichier de directives Runtime (. rd. Xml).</span><span class="sxs-lookup"><span data-stu-id="95a8c-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="95a8c-148">En outre, dans certains cas, le compilateur .NET Native n’est pas en mesure de déterminer les métadonnées qui doivent être disponibles pour la réflexion et s’appuie sur les indicateurs, notamment dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="95a8c-149">Certaines constructions telles que <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> et <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> ne peuvent pas être déterminées de manière statique.</span><span class="sxs-lookup"><span data-stu-id="95a8c-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="95a8c-150">Comme le compilateur ne peut pas déterminer les instanciations, un type générique à réfléchir doit être spécifié par les directives runtime.</span><span class="sxs-lookup"><span data-stu-id="95a8c-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="95a8c-151">Cela est nécessaire à double titre : tout le code doit être inclus, et la réflexion de types génériques peut former un cycle infini (par exemple, quand une méthode générique est appelée sur un type générique).</span><span class="sxs-lookup"><span data-stu-id="95a8c-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="95a8c-152">Les directives runtime sont définies dans un fichier de directives runtime (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="95a8c-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="95a8c-153">Pour obtenir des informations générales sur l’utilisation de ce fichier, consultez la rubrique [Bien démarrer](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="95a8c-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="95a8c-154">Pour plus d’informations sur les directives runtime, consultez [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="95a8c-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="95a8c-155">.NET Native comprend également des outils de profilage qui permettent au développeur de déterminer quels types en dehors du jeu par défaut doivent prendre en charge la réflexion.</span><span class="sxs-lookup"><span data-stu-id="95a8c-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="95a8c-156">Autres différences en matière de réflexion</span><span class="sxs-lookup"><span data-stu-id="95a8c-156">Other reflection-related differences</span></span>

<span data-ttu-id="95a8c-157">Il existe un certain nombre d’autres différences de comportement liées à la réflexion entre le .NET pour les applications du Windows Store et les .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="95a8c-158">Dans .NET Native :</span><span class="sxs-lookup"><span data-stu-id="95a8c-158">In .NET Native:</span></span>

- <span data-ttu-id="95a8c-159">La réflexion privée de types et de membres de la bibliothèque de classes .NET Framework n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="95a8c-160">Vous pouvez, toutefois, réfléchir vos propres types et membres privés, ainsi que les types et les membres dans des bibliothèques tierces.</span><span class="sxs-lookup"><span data-stu-id="95a8c-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="95a8c-161">La propriété <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> retourne correctement `false` pour un objet <xref:System.Reflection.ParameterInfo> qui représente une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="95a8c-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="95a8c-162">Dans .NET pour les applications du Windows Store, elle retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="95a8c-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="95a8c-163">Le langage intermédiaire ne prend pas cela en charge directement et l'interprétation est laissée au langage.</span><span class="sxs-lookup"><span data-stu-id="95a8c-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="95a8c-164">Les membres publics sur les structures <xref:System.RuntimeFieldHandle> et <xref:System.RuntimeMethodHandle> ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="95a8c-165">Ces types sont pris en charge uniquement pour LINQ, les arborescences d'expression et l'initialisation de tableau statique.</span><span class="sxs-lookup"><span data-stu-id="95a8c-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="95a8c-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> et <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> comprennent des membres masqués dans des classes de base et peuvent donc être remplacés sans substitutions explicites.</span><span class="sxs-lookup"><span data-stu-id="95a8c-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="95a8c-167">Cela vaut également pour les autres méthodes [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) .</span><span class="sxs-lookup"><span data-stu-id="95a8c-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="95a8c-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>et <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> n’échouent pas lorsque vous essayez de créer certaines combinaisons (par exemple, un tableau d' `byref` objets).</span><span class="sxs-lookup"><span data-stu-id="95a8c-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="95a8c-169">Vous ne pouvez pas utiliser la réflexion pour appeler des membres qui ont des paramètres de pointeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="95a8c-170">Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="95a8c-171">Lorsque le nombre d’arguments est incorrect et que le type de l’un des arguments est incorrect, .NET Native lève une exception <xref:System.ArgumentException> au lieu d’un <xref:System.Reflection.TargetParameterCountException> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="95a8c-172">La sérialisation binaire des exceptions n'est généralement pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="95a8c-173">Ainsi, les objets non sérialisables peuvent être ajoutés au dictionnaire <xref:System.Exception.Data%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="95a8c-174">API et scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="95a8c-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="95a8c-175">Les sections suivantes répertorient les API et les scénarios non pris en charge pour le développement général, l'interopérabilité et les technologies telles que HTTPClient et Windows Communication Foundation (WCF) :</span><span class="sxs-lookup"><span data-stu-id="95a8c-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="95a8c-176">Développement général</span><span class="sxs-lookup"><span data-stu-id="95a8c-176">General development</span></span>](#General)

- [<span data-ttu-id="95a8c-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="95a8c-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="95a8c-178">Interop</span><span class="sxs-lookup"><span data-stu-id="95a8c-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="95a8c-179">API non prises en charge</span><span class="sxs-lookup"><span data-stu-id="95a8c-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="95a8c-180">Différences de développement général</span><span class="sxs-lookup"><span data-stu-id="95a8c-180">General development differences</span></span>

<span data-ttu-id="95a8c-181">**Types de valeur**</span><span class="sxs-lookup"><span data-stu-id="95a8c-181">**Value types**</span></span>

- <span data-ttu-id="95a8c-182">Si vous substituez les méthodes <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> et <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> pour un type de valeur, n'appelez pas les implémentations de classe de base.</span><span class="sxs-lookup"><span data-stu-id="95a8c-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="95a8c-183">Dans .NET pour les applications du Windows Store, ces méthodes reposent sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="95a8c-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="95a8c-184">Au moment de la compilation, .NET Native génère une implémentation qui ne repose pas sur la réflexion du Runtime.</span><span class="sxs-lookup"><span data-stu-id="95a8c-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="95a8c-185">Cela signifie que si vous ne substituez pas ces deux méthodes, elles fonctionneront comme prévu, car .NET Native génère l’implémentation au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="95a8c-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="95a8c-186">Toutefois, la substitution de ces méthodes tout en appelant l'implémentation de la classe de base entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="95a8c-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="95a8c-187">Les types de valeur supérieurs à 1 mégaoctet ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-187">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="95a8c-188">Les types valeur ne peuvent pas avoir de constructeur sans paramètre dans .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="95a8c-189">(C# et Visual Basic interdisent les constructeurs sans paramètre sur les types valeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="95a8c-190">Toutefois, ceux-ci peuvent être créés dans un langage intermédiaire.)</span><span class="sxs-lookup"><span data-stu-id="95a8c-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="95a8c-191">**Tableaux**</span><span class="sxs-lookup"><span data-stu-id="95a8c-191">**Arrays**</span></span>

- <span data-ttu-id="95a8c-192">Les tableaux présentant une limite inférieure différente de zéro ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="95a8c-193">En règle générale, ces tableaux sont créés en appelant la surcharge <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="95a8c-194">La création dynamique de tableaux multidimensionnels n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="95a8c-195">Ces tableaux sont généralement créés en appelant une surcharge de la méthode <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> qui inclut un paramètre `lengths` , ou en appelant la méthode <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="95a8c-196">Les tableaux multidimensionnels qui ont quatre dimensions ou plus ne sont pas pris en charge ; il s'agit de tableaux dont la propriété <xref:System.Array.Rank%2A?displayProperty=nameWithType> à une valeur supérieure ou égale à quatre.</span><span class="sxs-lookup"><span data-stu-id="95a8c-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="95a8c-197">Utilisez des [tableaux en escalier](../../csharp/programming-guide/arrays/jagged-arrays.md) (tableaux de tableaux) à la place.</span><span class="sxs-lookup"><span data-stu-id="95a8c-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="95a8c-198">Par exemple, `array[x,y,z]` n'est pas valide, contrairement à `array[x][y][z]` .</span><span class="sxs-lookup"><span data-stu-id="95a8c-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="95a8c-199">L'écart entre les tableaux multidimensionnels n'est pas pris en charge et provoque une exception <xref:System.InvalidCastException> au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="95a8c-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="95a8c-200">**Génériques**</span><span class="sxs-lookup"><span data-stu-id="95a8c-200">**Generics**</span></span>

- <span data-ttu-id="95a8c-201">Une extension de type générique infinie entraîne une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="95a8c-202">Par exemple, la compilation de ce code échoue :</span><span class="sxs-lookup"><span data-stu-id="95a8c-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="95a8c-203">**Pointeurs**</span><span class="sxs-lookup"><span data-stu-id="95a8c-203">**Pointers**</span></span>

- <span data-ttu-id="95a8c-204">Les tableaux de pointeurs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="95a8c-205">Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="95a8c-206">**Sérialisation**</span><span class="sxs-lookup"><span data-stu-id="95a8c-206">**Serialization**</span></span>

<span data-ttu-id="95a8c-207">L'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="95a8c-208">Utilisez plutôt l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="95a8c-209">**Ressources**</span><span class="sxs-lookup"><span data-stu-id="95a8c-209">**Resources**</span></span>

<span data-ttu-id="95a8c-210">L'utilisation de ressources localisées avec la classe <xref:System.Diagnostics.Tracing.EventSource> n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="95a8c-211">La propriété <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> ne définit pas de ressources localisées.</span><span class="sxs-lookup"><span data-stu-id="95a8c-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="95a8c-212">**Délégués**</span><span class="sxs-lookup"><span data-stu-id="95a8c-212">**Delegates**</span></span>

<span data-ttu-id="95a8c-213">`Delegate.BeginInvoke` et `Delegate.EndInvoke` ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="95a8c-214">**API diverses**</span><span class="sxs-lookup"><span data-stu-id="95a8c-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="95a8c-215">La propriété [TypeInfo. Guid](xref:System.Type.GUID) lève une <xref:System.PlatformNotSupportedException> exception si un <xref:System.Runtime.InteropServices.GuidAttribute> attribut n’est pas appliqué au type.</span><span class="sxs-lookup"><span data-stu-id="95a8c-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="95a8c-216">Le GUID est utilisé principalement pour la prise en charge de COM.</span><span class="sxs-lookup"><span data-stu-id="95a8c-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="95a8c-217">La <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> méthode analyse correctement les chaînes qui contiennent des dates courtes dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="95a8c-218">Toutefois, elle n’assure pas la compatibilité avec les changements apportés à l’analyse des dates et heures, décrits dans les articles de la Base de connaissances Microsoft [KB2803771](https://support.microsoft.com/kb/2803771) et [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="95a8c-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="95a8c-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`est correctement arrondi dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="95a8c-220">Dans certaines versions du CLR, la chaîne de résultat est tronquée et non arrondie.</span><span class="sxs-lookup"><span data-stu-id="95a8c-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="95a8c-221">Différences pour HttpClient</span><span class="sxs-lookup"><span data-stu-id="95a8c-221">HttpClient differences</span></span>

<span data-ttu-id="95a8c-222">Dans .NET Native, la <xref:System.Net.Http.HttpClientHandler> classe utilise en interne WinINet (via la <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe) au lieu des <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> classes et utilisées dans le .NET standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="95a8c-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="95a8c-223">WinINet ne prend pas en charge toutes les options de configuration prises en charge par la classe <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="95a8c-224">Par conséquent :</span><span class="sxs-lookup"><span data-stu-id="95a8c-224">As a result:</span></span>

- <span data-ttu-id="95a8c-225">Certaines des propriétés de fonctionnalité lors du <xref:System.Net.Http.HttpClientHandler> retour `false` sur .net native, alors qu’elles retournent `true` dans le .NET standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="95a8c-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="95a8c-226">Certains accesseurs de propriété de configuration `get` retournent toujours une valeur fixe sur .net native qui est différente de la valeur configurable par défaut dans .net pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="95a8c-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="95a8c-227">Certaines différences de comportement supplémentaires sont décrites dans les sous-sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="95a8c-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="95a8c-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="95a8c-228">**Proxy**</span></span>

<span data-ttu-id="95a8c-229">La <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe ne prend pas en charge la configuration ou la substitution du proxy en fonction de la demande.</span><span class="sxs-lookup"><span data-stu-id="95a8c-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="95a8c-230">Cela signifie que toutes les demandes sur .NET Native utilisent le serveur proxy configuré par le système ou aucun serveur proxy, en fonction de la valeur de la <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="95a8c-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="95a8c-231">Dans .NET pour les applications du Windows Store, le serveur proxy est défini par la propriété <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="95a8c-232">Sur .NET Native, l’affectation <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> d’une valeur autre que `null` lève une <xref:System.PlatformNotSupportedException> exception.</span><span class="sxs-lookup"><span data-stu-id="95a8c-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="95a8c-233">La <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> propriété retourne `false` sur .net native, alors qu’elle retourne `true` dans le .NET Framework standard pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="95a8c-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="95a8c-234">**Redirection automatique**</span><span class="sxs-lookup"><span data-stu-id="95a8c-234">**Automatic redirection**</span></span>

<span data-ttu-id="95a8c-235">La <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe n’autorise pas la configuration du nombre maximal de redirections automatiques.</span><span class="sxs-lookup"><span data-stu-id="95a8c-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="95a8c-236">La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> est 50 par défaut dans la version .NET standard pour les applications du Windows Store et peut être modifiée.</span><span class="sxs-lookup"><span data-stu-id="95a8c-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="95a8c-237">Sur .NET Native, la valeur de cette propriété est 10 et la tentative de modification lève une <xref:System.PlatformNotSupportedException> exception.</span><span class="sxs-lookup"><span data-stu-id="95a8c-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="95a8c-238">La <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> propriété retourne `false` sur .net native, alors qu’elle retourne `true` dans .net pour les applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="95a8c-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="95a8c-239">**Décompression automatique**</span><span class="sxs-lookup"><span data-stu-id="95a8c-239">**Automatic decompression**</span></span>

<span data-ttu-id="95a8c-240">.NET pour les applications du Windows Store vous permet de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> sur <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>, ou sur <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="95a8c-241">.NET Native ne prend en charge que <xref:System.Net.DecompressionMethods.Deflate> avec <xref:System.Net.DecompressionMethods.GZip> , ou <xref:System.Net.DecompressionMethods.None> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="95a8c-242">Si vous essayez de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> uniquement sur <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> , elle est automatiquement définie à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="95a8c-243">**Internes**</span><span class="sxs-lookup"><span data-stu-id="95a8c-243">**Cookies**</span></span>

<span data-ttu-id="95a8c-244">La gestion des cookies est effectuée simultanément par <xref:System.Net.Http.HttpClient> et WinINet.</span><span class="sxs-lookup"><span data-stu-id="95a8c-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="95a8c-245">Les cookies de <xref:System.Net.CookieContainer> sont combinés aux cookies du cache de cookies WinINet.</span><span class="sxs-lookup"><span data-stu-id="95a8c-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="95a8c-246">La suppression d'un cookie de <xref:System.Net.CookieContainer> empêche <xref:System.Net.Http.HttpClient> de l'envoyer, mais si le cookie a déjà été vu par WinINet et que les cookies n'ont pas été supprimés par l'utilisateur, WinInet l'envoie.</span><span class="sxs-lookup"><span data-stu-id="95a8c-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="95a8c-247">Il est impossible de supprimer par programmation un cookie de WinINet à l'aide de l'API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>ou <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="95a8c-248">Définir la propriété <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> sur `false` entraîne uniquement l'arrêt de l'envoi des cookies par <xref:System.Net.Http.HttpClient> ; WinINet peut toujours inclure ses cookies dans la demande.</span><span class="sxs-lookup"><span data-stu-id="95a8c-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="95a8c-249">**Informations d'identification**</span><span class="sxs-lookup"><span data-stu-id="95a8c-249">**Credentials**</span></span>

<span data-ttu-id="95a8c-250">Dans .NET pour les applications du Windows Store, les propriétés <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> fonctionnent de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="95a8c-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="95a8c-251">En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> accepte tout objet qui implémente l'interface <xref:System.Net.ICredentials> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="95a8c-252">Dans .NET Native, l’affectation de la valeur à la <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> propriété `true` entraîne l’activation <xref:System.Net.Http.HttpClientHandler.Credentials%2A> de la propriété `null` .</span><span class="sxs-lookup"><span data-stu-id="95a8c-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="95a8c-253">En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> peut être définie uniquement sur `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>ou un objet de type <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="95a8c-254">L'affectation de tout autre objet <xref:System.Net.ICredentials> , le plus courant étant <xref:System.Net.CredentialCache>, à la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lève une <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="95a8c-255">**Autres fonctionnalités non prises en charge ou non configurables**</span><span class="sxs-lookup"><span data-stu-id="95a8c-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="95a8c-256">Dans .NET Native :</span><span class="sxs-lookup"><span data-stu-id="95a8c-256">In .NET Native:</span></span>

- <span data-ttu-id="95a8c-257">La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> est toujours <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="95a8c-258">Dans .NET pour les applications du Windows Store, la valeur par défaut est <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="95a8c-259">La propriété <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> n'est pas configurable.</span><span class="sxs-lookup"><span data-stu-id="95a8c-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="95a8c-260">La propriété <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> a toujours la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="95a8c-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="95a8c-261">Dans .NET pour les applications du Windows Store, la valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="95a8c-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="95a8c-262">L'en-tête `SetCookie2` dans les réponses est ignoré, car considéré comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="95a8c-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="95a8c-263">Différences concernant l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="95a8c-263">Interop differences</span></span>
 <span data-ttu-id="95a8c-264">**API déconseillées**</span><span class="sxs-lookup"><span data-stu-id="95a8c-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="95a8c-265">Un certain nombre d'API peu utilisées pour l'interopérabilité avec du code managé ont été déconseillées.</span><span class="sxs-lookup"><span data-stu-id="95a8c-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="95a8c-266">En cas d’utilisation avec .NET Native, ces API peuvent lever une <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> exception ou, ou entraîner une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="95a8c-267">Dans .NET pour les applications du Windows Store, ces API sont marquées comme obsolètes, même si les appeler génère un avertissement, plutôt qu'une erreur, du compilateur.</span><span class="sxs-lookup"><span data-stu-id="95a8c-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="95a8c-268">Les API déconseillées pour le `VARIANT` marshaling sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="95a8c-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="95a8c-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>est pris en charge, mais lève une exception dans certains scénarios, par exemple quand il est utilisé avec [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ou des `byref` variants.</span><span class="sxs-lookup"><span data-stu-id="95a8c-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="95a8c-270">Les API déconseillées pour la prise en charge [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) incluent :</span><span class="sxs-lookup"><span data-stu-id="95a8c-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="95a8c-271">Les API déconseillées pour les événements COM classiques sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="95a8c-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="95a8c-272">Les API déconseillées dans l' <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, qui ne sont pas prises en charge dans .net native, incluent :</span><span class="sxs-lookup"><span data-stu-id="95a8c-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="95a8c-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="95a8c-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="95a8c-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="95a8c-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="95a8c-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="95a8c-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="95a8c-276">Les autres fonctionnalités d’interopérabilité non prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="95a8c-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="95a8c-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="95a8c-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="95a8c-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(tous les membres)</span><span class="sxs-lookup"><span data-stu-id="95a8c-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="95a8c-279">API de marshaling rarement utilisées :</span><span class="sxs-lookup"><span data-stu-id="95a8c-279">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="95a8c-280">**Appel de plateforme et compatibilité avec l'interopérabilité COM**</span><span class="sxs-lookup"><span data-stu-id="95a8c-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="95a8c-281">La plupart des scénarios d’appel de code non managé et de COM Interop sont toujours pris en charge dans .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="95a8c-282">En particulier, toute l'interopérabilité avec les API Windows Runtime (WinRT) et tout le marshaling nécessaire pour le Windows Runtime sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="95a8c-283">Cela inclut la prise en charge du marshaling pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="95a8c-284">Tableaux (y compris <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="95a8c-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="95a8c-285">Délégués</span><span class="sxs-lookup"><span data-stu-id="95a8c-285">Delegates</span></span>

- <span data-ttu-id="95a8c-286">Chaînes (Unicode, Ansi et HSTRING)</span><span class="sxs-lookup"><span data-stu-id="95a8c-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="95a8c-287">Structures (`byref` et `byval`)</span><span class="sxs-lookup"><span data-stu-id="95a8c-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="95a8c-288">Unions</span><span class="sxs-lookup"><span data-stu-id="95a8c-288">Unions</span></span>

- <span data-ttu-id="95a8c-289">Handles Win32</span><span class="sxs-lookup"><span data-stu-id="95a8c-289">Win32 handles</span></span>

- <span data-ttu-id="95a8c-290">Toutes les constructions WinRT</span><span class="sxs-lookup"><span data-stu-id="95a8c-290">All WinRT constructs</span></span>

- <span data-ttu-id="95a8c-291">Prise en charge partielle du marshaling des types variant.</span><span class="sxs-lookup"><span data-stu-id="95a8c-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="95a8c-292">Les constructions suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="95a8c-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="95a8c-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="95a8c-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="95a8c-294">Toutefois, .NET Native ne prend pas en charge les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="95a8c-295">L'utilisation d'événements COM classiques</span><span class="sxs-lookup"><span data-stu-id="95a8c-295">Using classic COM events</span></span>

- <span data-ttu-id="95a8c-296">La mise en œuvre de l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> sur un type managé</span><span class="sxs-lookup"><span data-stu-id="95a8c-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="95a8c-297">L’implémentation de l’interface [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) sur un type managé via l’attribut <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="95a8c-298">Toutefois, vous ne pouvez pas appeler des objets COM via `IDispatch` , et votre objet managé ne peut pas implémenter `IDispatch` .</span><span class="sxs-lookup"><span data-stu-id="95a8c-298">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="95a8c-299">Utiliser la réflexion pour appeler une méthode d'appel de plateforme n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="95a8c-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="95a8c-300">Vous pouvez contourner cette limitation en encapsulant l'appel de méthode dans une autre méthode et en utilisant la réflexion pour appeler le wrapper.</span><span class="sxs-lookup"><span data-stu-id="95a8c-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="95a8c-301">Autres différences par rapport aux API .NET pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="95a8c-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="95a8c-302">Cette section répertorie les API restantes qui ne sont pas prises en charge dans .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="95a8c-303">Le plus grand ensemble d’API non prises en charge est l’API Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95a8c-303">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="95a8c-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="95a8c-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="95a8c-305">Les types dans les <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> espaces de noms et ne sont pas pris en charge dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="95a8c-306">Celles-ci incluent les types suivants qui sont présents dans .NET pour les applications du Windows Store pour Windows 8 :</span><span class="sxs-lookup"><span data-stu-id="95a8c-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="95a8c-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="95a8c-307">**Visual Basic**</span></span>

<span data-ttu-id="95a8c-308">Visual Basic n’est actuellement pas pris en charge dans .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="95a8c-309">Les types suivants dans les <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> espaces de noms et ne sont pas disponibles dans .net Native :</span><span class="sxs-lookup"><span data-stu-id="95a8c-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="95a8c-310">**Contexte de réflexion (espace de noms System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="95a8c-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="95a8c-311">La <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> classe n’est pas prise en charge dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="95a8c-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="95a8c-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="95a8c-313">La `System.Net.Http.RtcRequestFactory` classe n’est pas prise en charge dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="95a8c-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="95a8c-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="95a8c-315">Les types des [espaces de noms System. ServiceModel. \*](xref:System.ServiceModel) ne sont pas pris en charge dans .net native.</span><span class="sxs-lookup"><span data-stu-id="95a8c-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="95a8c-316">Il s’agit notamment des types suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-316">These include the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="95a8c-317">Différences entre les sérialiseurs</span><span class="sxs-lookup"><span data-stu-id="95a8c-317">Differences in serializers</span></span>

<span data-ttu-id="95a8c-318">Les différences suivantes concernent la sérialisation et la désérialisation avec les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>et <xref:System.Xml.Serialization.XmlSerializer> :</span><span class="sxs-lookup"><span data-stu-id="95a8c-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="95a8c-319">Dans .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser ou désérialiser une classe dérivée qui a un membre de classe de base dont le type n’est pas un type de sérialisation racine.</span><span class="sxs-lookup"><span data-stu-id="95a8c-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="95a8c-320">Par exemple, dans le code suivant, sérialiser ou désérialiser `Y` génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="95a8c-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="95a8c-321">Le type `InnerType` n'est pas connu du sérialiseur, car les membres de la classe de base ne sont pas parcourus pendant la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="95a8c-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="95a8c-322"><xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser une classe ou une structure qui implémente l'interface <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="95a8c-323">Par exemple, les types suivants ne parviennent pas à sérialiser ou à désérialiser :</span><span class="sxs-lookup"><span data-stu-id="95a8c-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="95a8c-324"><xref:System.Xml.Serialization.XmlSerializer> ne sérialise pas la valeur d'objet suivante, car il ne connaît pas le type exact de l'objet à sérialiser :</span><span class="sxs-lookup"><span data-stu-id="95a8c-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="95a8c-325"><xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à sérialiser ou à désérialiser si le type de l'objet sérialisé est <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="95a8c-326">Tous les sérialiseurs (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>et <xref:System.Xml.Serialization.XmlSerializer>) ne parviennent pas à générer un code de sérialisation pour un type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ou pour un type contenant <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="95a8c-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="95a8c-327">Ils affichent des erreurs de génération à la place.</span><span class="sxs-lookup"><span data-stu-id="95a8c-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="95a8c-328">Les constructeurs suivants des types de sérialisation ne fonctionnent pas nécessairement comme prévu :</span><span class="sxs-lookup"><span data-stu-id="95a8c-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="95a8c-329"><xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à générer le code pour un type dont les méthodes possèdent un des attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="95a8c-330"><xref:System.Xml.Serialization.XmlSerializer> ne traite pas l'interface de sérialisation personnalisée <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="95a8c-331">Si vous avez une classe qui implémente cette interface, <xref:System.Xml.Serialization.XmlSerializer> considère le type comme un ancien objet CLR simple et sérialise uniquement ses propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="95a8c-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="95a8c-332">La sérialisation d’un <xref:System.Exception> objet brut ne fonctionne pas correctement avec <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="95a8c-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="95a8c-333">Différences concernant Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95a8c-333">Visual Studio differences</span></span>

<span data-ttu-id="95a8c-334">**Exceptions et débogage**</span><span class="sxs-lookup"><span data-stu-id="95a8c-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="95a8c-335">Quand vous exécutez des applications compilées à l’aide de .NET Native dans le débogueur, les exceptions de première chance sont activées pour les types d’exception suivants :</span><span class="sxs-lookup"><span data-stu-id="95a8c-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="95a8c-336">**Génération d'applications**</span><span class="sxs-lookup"><span data-stu-id="95a8c-336">**Building apps**</span></span>

<span data-ttu-id="95a8c-337">Recourez aux outils de génération x86 qui sont utilisés par défaut par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95a8c-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="95a8c-338">Nous vous déconseillons d'utiliser les outils MSBuild AMD64, qui se trouvent dans C:\Program Files (x86)\MSBuild\12.0\bin\amd64, car ils peuvent créer des problèmes de génération.</span><span class="sxs-lookup"><span data-stu-id="95a8c-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="95a8c-339">**Profileurs**</span><span class="sxs-lookup"><span data-stu-id="95a8c-339">**Profilers**</span></span>

- <span data-ttu-id="95a8c-340">Le profileur d'UC Visual Studio et le profileur de mémoire XAML n'affichent pas Uniquement mon code correctement.</span><span class="sxs-lookup"><span data-stu-id="95a8c-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="95a8c-341">Le profileur de mémoire XAML n'affiche pas avec précision les données du tas managé.</span><span class="sxs-lookup"><span data-stu-id="95a8c-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="95a8c-342">Le profileur d'UC ne peut pas identifier correctement les modules, et affiche les noms de fonction avec préfixe.</span><span class="sxs-lookup"><span data-stu-id="95a8c-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="95a8c-343">**Projets de bibliothèque de tests unitaires**</span><span class="sxs-lookup"><span data-stu-id="95a8c-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="95a8c-344">L’activation de .NET Native sur une bibliothèque de tests unitaires pour un projet d’applications du Windows Store n’est pas prise en charge et entraîne l’échec de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="95a8c-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="95a8c-345">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95a8c-345">See also</span></span>

- [<span data-ttu-id="95a8c-346">Prise en main</span><span class="sxs-lookup"><span data-stu-id="95a8c-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="95a8c-347">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="95a8c-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="95a8c-348">Vue d’ensemble de .NET pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="95a8c-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="95a8c-349">Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="95a8c-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
