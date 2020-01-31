---
title: Meilleures pratiques pour l’interopérabilité native – .NET
description: Découvrez les meilleures pratiques pour interagir avec des composants natifs en .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 9486256b815856c0c283f5fe231be3d35d6e8f00
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742753"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="eefc1-103">Meilleures pratiques pour l’interopérabilité native</span><span class="sxs-lookup"><span data-stu-id="eefc1-103">Native interoperability best practices</span></span>

<span data-ttu-id="eefc1-104">.NET propose différents moyens de personnaliser du code d’interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="eefc1-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="eefc1-105">Cet article détaille les instructions suivies par les équipes .NET de Microsoft pour l’interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="eefc1-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="eefc1-106">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="eefc1-106">General guidance</span></span>

<span data-ttu-id="eefc1-107">Les instructions de cette section s’appliquent à tous les scénarios d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="eefc1-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="eefc1-108">✔️ Utilisez le même nom et la même mise en majuscules pour vos méthodes et paramètres que la méthode Native que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="eefc1-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="eefc1-109">✔️ envisagez d’utiliser le même nom et la même mise en majuscules pour les valeurs constantes.</span><span class="sxs-lookup"><span data-stu-id="eefc1-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="eefc1-110">✔️ Utilisez les types .NET qui se mappent le plus près du type natif.</span><span class="sxs-lookup"><span data-stu-id="eefc1-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="eefc1-111">Par exemple, en C#, utilisez `uint` lorsque le type natif est `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="eefc1-112">✔️ N’utilisez que des attributs `[In]` et `[Out]` lorsque le comportement que vous recherchez diffère du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="eefc1-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="eefc1-113">✔️ envisagez d’utiliser <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pour regrouper vos mémoires tampons de tableau natives.</span><span class="sxs-lookup"><span data-stu-id="eefc1-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="eefc1-114">✔️ Encapsulez vos déclarations P/Invoke dans une classe portant le même nom et en respectant la casse que votre bibliothèque native.</span><span class="sxs-lookup"><span data-stu-id="eefc1-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="eefc1-115">Vos attributs `[DllImport]` pourront ainsi utiliser la fonctionnalité `nameof` du langage C# pour transmettre le nom de la bibliothèque native et vérifier qu’il ne comporte pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eefc1-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="eefc1-116">Paramètres des attributs DllImport</span><span class="sxs-lookup"><span data-stu-id="eefc1-116">DllImport attribute settings</span></span>

| <span data-ttu-id="eefc1-117">Paramètre</span><span class="sxs-lookup"><span data-stu-id="eefc1-117">Setting</span></span> | <span data-ttu-id="eefc1-118">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="eefc1-118">Default</span></span> | <span data-ttu-id="eefc1-119">Recommandation</span><span class="sxs-lookup"><span data-stu-id="eefc1-119">Recommendation</span></span> | <span data-ttu-id="eefc1-120">Détails</span><span class="sxs-lookup"><span data-stu-id="eefc1-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="eefc1-121">Conserver la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="eefc1-121">keep default</span></span>  | <span data-ttu-id="eefc1-122">S’il est défini explicitement sur false, les valeurs de retour HRESULT en échec sont converties en exceptions (et la valeur de retour de la définition devient ainsi Null).</span><span class="sxs-lookup"><span data-stu-id="eefc1-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="eefc1-123">Dépend de l'API</span><span class="sxs-lookup"><span data-stu-id="eefc1-123">depends on the API</span></span>  | <span data-ttu-id="eefc1-124">Définissez-le sur true si l’API utilise GetLastError et Marshal.GetLastWin32Error pour obtenir la valeur.</span><span class="sxs-lookup"><span data-stu-id="eefc1-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="eefc1-125">Si l’API définit une condition indiquant une erreur, récupérez l’erreur avant d’effectuer d’autres appels, de façon à éviter de la remplacer par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="eefc1-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="eefc1-126">`CharSet.None`, qui bascule en secours vers le comportement `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="eefc1-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="eefc1-127">Utilisez explicitement `CharSet.Unicode` ou `CharSet.Ansi` lorsque des chaînes ou des caractères sont présents dans la définition</span><span class="sxs-lookup"><span data-stu-id="eefc1-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="eefc1-128">Cela permet de spécifier le comportement de marshaling des chaînes et le rôle de `ExactSpelling` quand la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="eefc1-129">Notez que `CharSet.Ansi` est en réalité UTF-8 sur Unix.</span><span class="sxs-lookup"><span data-stu-id="eefc1-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="eefc1-130">_La plupart du temps_, Windows utilise Unicode et Unix UTF-8.</span><span class="sxs-lookup"><span data-stu-id="eefc1-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="eefc1-131">Pour plus d'informations, voir la [documentation sur les charsets](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="eefc1-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="eefc1-132">Définissez-le sur true pour augmenter légèrement les performances. En effet, le runtime ne recherche pas de noms de fonctions de remplacement avec un suffixe « A » ou « W » selon la valeur du paramètre `CharSet` (« A » pour `CharSet.Ansi` et « W » pour `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="eefc1-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="eefc1-133">Paramètres de chaînes</span><span class="sxs-lookup"><span data-stu-id="eefc1-133">String parameters</span></span>

<span data-ttu-id="eefc1-134">Lorsque le jeu de caractères est Unicode ou que l’argument est explicitement marqué comme `[MarshalAs(UnmanagedType.LPWSTR)]` _et_ que la chaîne est passée par valeur (non `ref` ou `out`), la chaîne est épinglée et utilisée directement par le code natif (au lieu d’être copiée).</span><span class="sxs-lookup"><span data-stu-id="eefc1-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="eefc1-135">N’oubliez pas de marquer `[DllImport]` comme `Charset.Unicode` sauf si vous souhaitez explicitement un traitement ANSI de vos chaînes.</span><span class="sxs-lookup"><span data-stu-id="eefc1-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="eefc1-136">❌ n’utilisez pas de paramètres de `[Out] string`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="eefc1-137">Les paramètres de chaînes passés en valeur avec l’attribut `[Out]` risquent de déstabiliser le runtime s’il s’agit de chaînes centralisées.</span><span class="sxs-lookup"><span data-stu-id="eefc1-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="eefc1-138">Pour plus d’informations sur la centralisation des chaînes, voir la documentation de <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eefc1-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="eefc1-139">❌ éviter les paramètres de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="eefc1-140">Le marshaling `StringBuilder` crée *toujours* une copie de la mémoire tampon native.</span><span class="sxs-lookup"><span data-stu-id="eefc1-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="eefc1-141">Il peut donc se révéler extrêmement inefficace.</span><span class="sxs-lookup"><span data-stu-id="eefc1-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="eefc1-142">Prenons le scénario classique d’appel d’une API Windows qui prend une chaîne :</span><span class="sxs-lookup"><span data-stu-id="eefc1-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="eefc1-143">Crée un SB de la capacité souhaitée (alloue la capacité gérée) **{1}**</span><span class="sxs-lookup"><span data-stu-id="eefc1-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="eefc1-144">Invoquer</span><span class="sxs-lookup"><span data-stu-id="eefc1-144">Invoke</span></span>
   1. <span data-ttu-id="eefc1-145">Alloue une mémoire tampon native **{2}**</span><span class="sxs-lookup"><span data-stu-id="eefc1-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="eefc1-146">Copie le contenu si `[In]` _(valeur par défaut pour un paramètre `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="eefc1-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="eefc1-147">Copie la mémoire tampon native dans un tableau managé nouvellement alloué si `[Out]` **{3}** _(également la valeur par défaut pour `StringBuilder`)_ .</span><span class="sxs-lookup"><span data-stu-id="eefc1-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="eefc1-148">`ToString()` alloue encore un autre tableau managé **{4}**</span><span class="sxs-lookup"><span data-stu-id="eefc1-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="eefc1-149">Soit *{4}* allocations pour extraire une chaîne du code natif.</span><span class="sxs-lookup"><span data-stu-id="eefc1-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="eefc1-150">Le mieux que l’on puisse faire pour réduire ce nombre est de réutiliser `StringBuilder` dans un autre appel, mais cela ne fait gagner que *1* allocation.</span><span class="sxs-lookup"><span data-stu-id="eefc1-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="eefc1-151">Il est largement préférable d’utiliser et de mettre en cache une mémoire tampon de caractères à partir de `ArrayPool` : vous pourrez limiter l’allocation à `ToString()` lors des appels suivants.</span><span class="sxs-lookup"><span data-stu-id="eefc1-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="eefc1-152">L’autre problème de `StringBuilder` est qu’il copie toujours la sauvegarde de la mémoire tampon de retour sur la première valeur Null.</span><span class="sxs-lookup"><span data-stu-id="eefc1-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="eefc1-153">Si la chaîne de retour transmise n’est pas terminée ou se termine par un double Null, P/Invoke est au mieux incorrect.</span><span class="sxs-lookup"><span data-stu-id="eefc1-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="eefc1-154">Si vous *utilisez*`StringBuilder`, le dernier piège est que la capacité n’inclut **pas** de valeur Null masquée, qui est toujours prise en compte dans l’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="eefc1-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="eefc1-155">Il est courant de se tromper de ce point de vue, car la plupart des API demandent la taille de la mémoire tampon valeur Null *incluse*.</span><span class="sxs-lookup"><span data-stu-id="eefc1-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="eefc1-156">Il en résulte parfois des allocations gaspillées/inutiles.</span><span class="sxs-lookup"><span data-stu-id="eefc1-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="eefc1-157">En outre, cet écueil empêche le runtime d’optimiser le marshaling `StringBuilder` afin de réduire les copies.</span><span class="sxs-lookup"><span data-stu-id="eefc1-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="eefc1-158">✔️ envisagez d’utiliser `char[]`s à partir d’un `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="eefc1-159">Pour plus d’informations sur le marshaling des chaînes, consultez [Marshaling par défaut pour les chaînes](../../framework/interop/default-marshaling-for-strings.md) et [Personnaliser le marshaling des chaînes](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="eefc1-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="eefc1-160">__Spécifique à Windows__ Pour les chaînes de `[Out]`, le CLR utilise `CoTaskMemFree` par défaut pour libérer des chaînes ou `SysStringFree` pour les chaînes marquées comme `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="eefc1-161">**Pour la plupart des API avec une mémoire tampon de chaîne de sortie :** Le nombre de caractères transmis doit inclure la valeur null.</span><span class="sxs-lookup"><span data-stu-id="eefc1-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="eefc1-162">Si la valeur de retour est inférieure au nombre de caractères transmis, c’est le signe que l’appel a réussi et que la valeur correspond au nombre de caractères *sans* la valeur Null de fin.</span><span class="sxs-lookup"><span data-stu-id="eefc1-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="eefc1-163">Sinon, le nombre représente la taille requise de la mémoire tampon caractère Null *inclus*.</span><span class="sxs-lookup"><span data-stu-id="eefc1-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="eefc1-164">Pass in 5, obtenir 4 : la chaîne comporte 4 caractères avec une valeur null de fin.</span><span class="sxs-lookup"><span data-stu-id="eefc1-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="eefc1-165">Pass in 5, obtenir 6 : la chaîne comporte 5 caractères, nécessite une mémoire tampon de 6 caractères pour contenir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="eefc1-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="eefc1-166">Types de données Windows pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="eefc1-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="eefc1-167">Paramètres et champs booléens</span><span class="sxs-lookup"><span data-stu-id="eefc1-167">Boolean parameters and fields</span></span>

<span data-ttu-id="eefc1-168">Il est facile de se perdre avec les booléens.</span><span class="sxs-lookup"><span data-stu-id="eefc1-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="eefc1-169">Par défaut, un `bool` .NET est marshalé en un `BOOL` Windows, où il s’agit d’une valeur de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="eefc1-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="eefc1-170">À l’inverse, les types `_Bool` et `bool` en C et C++ correspondent à un *seul* octet.</span><span class="sxs-lookup"><span data-stu-id="eefc1-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="eefc1-171">Il peut alors être difficile de traquer les bogues, car la valeur de retour est à moitié ignorée, ce qui ne modifie que *potentiellement* le résultat.</span><span class="sxs-lookup"><span data-stu-id="eefc1-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="eefc1-172">Pour plus d’informations sur le marshaling des valeurs `bool` .NET en types `bool` C ou C++, consultez la documentation [Personnaliser le marshaling des champs booléens](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="eefc1-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="eefc1-173">GUID</span><span class="sxs-lookup"><span data-stu-id="eefc1-173">GUIDs</span></span>

<span data-ttu-id="eefc1-174">Les GUID sont directement utilisables dans les signatures.</span><span class="sxs-lookup"><span data-stu-id="eefc1-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="eefc1-175">De nombreuses API Windows acceptent des alias de type `GUID&` comme `REFIID`,</span><span class="sxs-lookup"><span data-stu-id="eefc1-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="eefc1-176">qui, s’ils sont passés en référence, peuvent être transmis par `ref` ou avec l’attribut `[MarshalAs(UnmanagedType.LPStruct)]`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="eefc1-177">GUID</span><span class="sxs-lookup"><span data-stu-id="eefc1-177">GUID</span></span> | <span data-ttu-id="eefc1-178">GUID en référence</span><span class="sxs-lookup"><span data-stu-id="eefc1-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="eefc1-179">❌ n’utilisez pas `[MarshalAs(UnmanagedType.LPStruct)]` pour tous les paramètres du GUID `ref`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="eefc1-180">Types blittables</span><span class="sxs-lookup"><span data-stu-id="eefc1-180">Blittable types</span></span>

<span data-ttu-id="eefc1-181">Les types blittables sont des types qui ont la même représentation au niveau du bit dans le code managé et dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="eefc1-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="eefc1-182">Il n’est donc pas nécessaire de les convertir dans un autre format pour les marshaler vers et à partir du code natif. Ils sont à privilégier en raison de l’amélioration des performances qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="eefc1-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="eefc1-183">**Types blittables :**</span><span class="sxs-lookup"><span data-stu-id="eefc1-183">**Blittable types:**</span></span>

- <span data-ttu-id="eefc1-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="eefc1-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="eefc1-185">Tableaux unidimensionnels non imbriqués de types blittables (par exemple, `int[]`)</span><span class="sxs-lookup"><span data-stu-id="eefc1-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="eefc1-186">Structs et classes à disposition fixe qui n’ont que des types valeurs blittables, par exemple les champs :</span><span class="sxs-lookup"><span data-stu-id="eefc1-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="eefc1-187">La disposition fixe exige `[StructLayout(LayoutKind.Sequential)]` ou `[StructLayout(LayoutKind.Explicit)]`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="eefc1-188">Les structs sont `LayoutKind.Sequential` par défaut, les classes `LayoutKind.Auto`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="eefc1-189">**Types NON blittables :**</span><span class="sxs-lookup"><span data-stu-id="eefc1-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="eefc1-190">**Types PARFOIS blittables :**</span><span class="sxs-lookup"><span data-stu-id="eefc1-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="eefc1-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="eefc1-191">`char`, `string`</span></span>

<span data-ttu-id="eefc1-192">Lorsque des types blittables sont passés en référence, ils sont simplement épinglés par le marshaleur, et non copiés vers une mémoire tampon intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="eefc1-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="eefc1-193">(Les classes sont, par nature, passées en référence ; les structs sont passés en référence lorsqu’ils sont utilisés avec `ref` ou `out`.)</span><span class="sxs-lookup"><span data-stu-id="eefc1-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="eefc1-194">Un `char` est blittable dans un tableau unidimensionnel **ou** s’il fait partie d’un type explicitement marqué `[StructLayout]` avec `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="eefc1-195">Une `string` est blittable si elle n’est pas contenue dans un autre type et qu’elle est passé en argument marqué `[MarshalAs(UnmanagedType.LPWStr)]` ou que `CharSet = CharSet.Unicode` est défini pour `[DllImport]`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="eefc1-196">Pour savoir si un type est blittable, essayez de créer un `GCHandle` épinglé.</span><span class="sxs-lookup"><span data-stu-id="eefc1-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="eefc1-197">Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="eefc1-198">✔️ faire en sorte que vos structures soient blittables si possible.</span><span class="sxs-lookup"><span data-stu-id="eefc1-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="eefc1-199">Pour plus d'informations, consultez .</span><span class="sxs-lookup"><span data-stu-id="eefc1-199">For more information, see:</span></span>

- [<span data-ttu-id="eefc1-200">Types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="eefc1-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="eefc1-201">Marshaling de types</span><span class="sxs-lookup"><span data-stu-id="eefc1-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="eefc1-202">Maintenir actifs les objets gérés</span><span class="sxs-lookup"><span data-stu-id="eefc1-202">Keeping managed objects alive</span></span>

<span data-ttu-id="eefc1-203">`GC.KeepAlive()` garantit qu'un objet reste accessible jusqu'à ce que la méthode KeepAlive soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="eefc1-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="eefc1-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) permet au marshaleur de maintenir un objet actif pendant la durée de P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="eefc1-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="eefc1-205">Il peut être utilisé à la place de `IntPtr` dans les signatures de méthode.</span><span class="sxs-lookup"><span data-stu-id="eefc1-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="eefc1-206">`SafeHandle` remplace cette classe et doit être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="eefc1-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="eefc1-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) permet d’épingler un objet géré et d’y associer le pointeur natif.</span><span class="sxs-lookup"><span data-stu-id="eefc1-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="eefc1-208">En voici le modèle de base :</span><span class="sxs-lookup"><span data-stu-id="eefc1-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="eefc1-209">L’épinglage n’est pas le comportement par défaut de `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="eefc1-210">L’autre grand modèle sert à faire passer une référence à un objet géré à travers le code natif, puis à nouveau au code managé, en général avec un rappel.</span><span class="sxs-lookup"><span data-stu-id="eefc1-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="eefc1-211">En voici le modèle :</span><span class="sxs-lookup"><span data-stu-id="eefc1-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="eefc1-212">N’oubliez pas que `GCHandle` doit être explicitement libéré pour éviter les fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="eefc1-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="eefc1-213">Types de données Windows courants</span><span class="sxs-lookup"><span data-stu-id="eefc1-213">Common Windows data types</span></span>

<span data-ttu-id="eefc1-214">Voici la liste des types de données courants dans les API Windows et des types C# à utiliser pour les appels dans le code Windows.</span><span class="sxs-lookup"><span data-stu-id="eefc1-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="eefc1-215">Malgré leur nom, les types suivants ont la même taille sur Windows 32 bits et 64 bits.</span><span class="sxs-lookup"><span data-stu-id="eefc1-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="eefc1-216">Largeur</span><span class="sxs-lookup"><span data-stu-id="eefc1-216">Width</span></span> | <span data-ttu-id="eefc1-217">Portail</span><span class="sxs-lookup"><span data-stu-id="eefc1-217">Windows</span></span>          | <span data-ttu-id="eefc1-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="eefc1-218">C (Windows)</span></span>          | <span data-ttu-id="eefc1-219">C#</span><span class="sxs-lookup"><span data-stu-id="eefc1-219">C#</span></span>       | <span data-ttu-id="eefc1-220">Alternative</span><span class="sxs-lookup"><span data-stu-id="eefc1-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="eefc1-221">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="eefc1-222">8</span><span class="sxs-lookup"><span data-stu-id="eefc1-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="eefc1-223">8</span><span class="sxs-lookup"><span data-stu-id="eefc1-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="eefc1-224">8</span><span class="sxs-lookup"><span data-stu-id="eefc1-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="eefc1-225">8</span><span class="sxs-lookup"><span data-stu-id="eefc1-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="eefc1-226">16</span><span class="sxs-lookup"><span data-stu-id="eefc1-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="eefc1-227">16</span><span class="sxs-lookup"><span data-stu-id="eefc1-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="eefc1-228">16</span><span class="sxs-lookup"><span data-stu-id="eefc1-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="eefc1-229">16</span><span class="sxs-lookup"><span data-stu-id="eefc1-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="eefc1-230">16</span><span class="sxs-lookup"><span data-stu-id="eefc1-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="eefc1-231">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="eefc1-232">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="eefc1-233">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="eefc1-234">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="eefc1-235">64</span><span class="sxs-lookup"><span data-stu-id="eefc1-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="eefc1-236">64</span><span class="sxs-lookup"><span data-stu-id="eefc1-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="eefc1-237">64</span><span class="sxs-lookup"><span data-stu-id="eefc1-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="eefc1-238">64</span><span class="sxs-lookup"><span data-stu-id="eefc1-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="eefc1-239">64</span><span class="sxs-lookup"><span data-stu-id="eefc1-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="eefc1-240">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="eefc1-241">32</span><span class="sxs-lookup"><span data-stu-id="eefc1-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="eefc1-242">Comme il s’agit de pointeurs, les types suivants suivent la largeur de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="eefc1-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="eefc1-243">Utilisez pour eux `IntPtr`/`UIntPtr`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="eefc1-244">Types de pointeurs signés (utilisez `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="eefc1-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="eefc1-245">Types de pointeurs non signés (utilisez `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="eefc1-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="eefc1-246">Un `PVOID` Windows, qui correspond à un `void*` C, peut être marshalé comme `IntPtr` ou `UIntPtr` ; préférez `void*` dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="eefc1-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="eefc1-247">Types de données Windows</span><span class="sxs-lookup"><span data-stu-id="eefc1-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="eefc1-248">Plages de types de données</span><span class="sxs-lookup"><span data-stu-id="eefc1-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="eefc1-249">Structures</span><span class="sxs-lookup"><span data-stu-id="eefc1-249">Structs</span></span>

<span data-ttu-id="eefc1-250">Les structs managés sont créés sur la pile et ne sont pas supprimés tant que la méthode n’a pas retourné de valeur.</span><span class="sxs-lookup"><span data-stu-id="eefc1-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="eefc1-251">Ils sont donc par définition « épinglés » (ils ne sont pas déplacés par le récupérateur de mémoire).</span><span class="sxs-lookup"><span data-stu-id="eefc1-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="eefc1-252">Vous pouvez aussi prendre simplement l’adresse dans des blocs de code unsafe si le code natif n’utilise pas le pointeur après la fin de la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="eefc1-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="eefc1-253">Les structs blittables sont beaucoup plus performants, car ils sont directement utilisables par la couche de marshaling.</span><span class="sxs-lookup"><span data-stu-id="eefc1-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="eefc1-254">Essayez de rendre les structs blittables (par exemple, évitez `bool`).</span><span class="sxs-lookup"><span data-stu-id="eefc1-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="eefc1-255">Pour plus d'informations, voir la section [Types blittables](#blittable-types).</span><span class="sxs-lookup"><span data-stu-id="eefc1-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="eefc1-256">*Si* le struct est blittable, utilisez `sizeof()` au lieu de `Marshal.SizeOf<MyStruct>()` pour obtenir de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="eefc1-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="eefc1-257">Comme nous l’avons mentionné plus haut, vous pouvez valider que le type est blittable en essayant de créer un `GCHandle` épinglé.</span><span class="sxs-lookup"><span data-stu-id="eefc1-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="eefc1-258">Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="eefc1-259">Les pointeurs vers des structs dans les définitions doivent être passés en `ref` ou utiliser `unsafe` et `*`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="eefc1-260">✔️ Faites correspondre le struct managé le plus fidèlement possible à la forme et aux noms utilisés dans la documentation ou l’en-tête officiel de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="eefc1-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="eefc1-261">✔️ Utilisez le `sizeof()` C# au lieu de `Marshal.SizeOf<MyStruct>()` pour les structures blittable afin d’améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="eefc1-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="eefc1-262">Un tableau comme `INT_PTR Reserved1[2]` doit être marshalé en deux champs `IntPtr`, `Reserved1a` et `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="eefc1-262">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="eefc1-263">Lorsque le tableau natif est un type primitif, il est possible d’utiliser le mot clé `fixed` pour que le code soit un peu plus propre.</span><span class="sxs-lookup"><span data-stu-id="eefc1-263">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="eefc1-264">Par exemple, `SYSTEM_PROCESS_INFORMATION` se présente ainsi dans l’en-tête natif :</span><span class="sxs-lookup"><span data-stu-id="eefc1-264">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="eefc1-265">On peut l’écrire ainsi en C# :</span><span class="sxs-lookup"><span data-stu-id="eefc1-265">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="eefc1-266">Toutefois, les mémoires tampons fixes présentent quelques pièges.</span><span class="sxs-lookup"><span data-stu-id="eefc1-266">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="eefc1-267">Les mémoires tampons fixes de types non blittables ne sont pas marshalées correctement ; par conséquent, le tableau sur place doit être étendu à plusieurs champs différents.</span><span class="sxs-lookup"><span data-stu-id="eefc1-267">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="eefc1-268">En outre, dans .NET Framework et .NET Core avant la version 3.0, si un struct contenant un champ de mémoire tampon fixe est imbriqué dans un struct non blittable, le champ de mémoire tampon fixe n’est pas marshalé correctement dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="eefc1-268">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
