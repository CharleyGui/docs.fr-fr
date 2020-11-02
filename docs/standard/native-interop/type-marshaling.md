---
title: Marshaling de types - .NET
description: Découvrez comment .NET marshale vos types en une représentation native.
ms.date: 01/18/2019
ms.openlocfilehash: bedaf49a5f7c5274f5e1bc7774490fec73651259
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188391"
---
# <a name="type-marshaling"></a><span data-ttu-id="dce58-103">Marshaling de types</span><span class="sxs-lookup"><span data-stu-id="dce58-103">Type marshaling</span></span>

<span data-ttu-id="dce58-104">Le **marshaling** est le processus qui consiste à transformer les types quand ils doivent naviguer entre du code managé et du code natif.</span><span class="sxs-lookup"><span data-stu-id="dce58-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="dce58-105">La raison pour laquelle le marshaling est nécessaire est que les types diffèrent entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="dce58-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="dce58-106">Dans le code managé, par exemple, vous avez un `String` , tandis que dans les chaînes universelles non managées peuvent être Unicode (« larges »), non-Unicode, terminé par null, ASCII, etc. Par défaut, le sous-système P/Invoke tente d’effectuer la bonne chose en fonction du comportement par défaut, décrit dans cet article.</span><span class="sxs-lookup"><span data-stu-id="dce58-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="dce58-107">Toutefois, dans les cas où vous avez besoin de plus de contrôle, vous pouvez employer l’attribut [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) pour spécifier le type attendu du côté du code non managé.</span><span class="sxs-lookup"><span data-stu-id="dce58-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="dce58-108">Par exemple, pour que la chaîne soit envoyée sous forme de chaîne ANSI terminée par Null, vous pouvez procéder ainsi :</span><span class="sxs-lookup"><span data-stu-id="dce58-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="dce58-109">Règles par défaut de marshaling des types courants</span><span class="sxs-lookup"><span data-stu-id="dce58-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="dce58-110">En règle générale, le runtime tente de prendre la bonne décision en matière de marshaling, c’est-à-dire celle qui demande le moins de travail de votre part.</span><span class="sxs-lookup"><span data-stu-id="dce58-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="dce58-111">Les tableaux suivants indiquent comment chaque type est marshalé par défaut lorsqu’il est utilisé dans un paramètre ou un champ.</span><span class="sxs-lookup"><span data-stu-id="dce58-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="dce58-112">Les types de caractères et d’entiers de longueur fixe C99/C ++11 garantissent que le tableau suivant est correct pour toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="dce58-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="dce58-113">Vous pouvez utiliser n’importe quel type natif ayant les mêmes exigence d’alignement et de taille que ces types.</span><span class="sxs-lookup"><span data-stu-id="dce58-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="dce58-114">Le premier tableau décrit les correspondances de différents types pour lesquels le marshaling P/Invoke et le marshaling des champs sont identiques.</span><span class="sxs-lookup"><span data-stu-id="dce58-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="dce58-115">Type .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-115">.NET Type</span></span> | <span data-ttu-id="dce58-116">Type natif</span><span class="sxs-lookup"><span data-stu-id="dce58-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="dce58-117">`char` ou `char16_t` selon le `CharSet` de P/Invoke ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="dce58-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="dce58-118">Voir la [documentation charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="dce58-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="dce58-119">`char*` ou `char16_t*` selon le `CharSet` de P/Invoke ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="dce58-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="dce58-120">Voir la [documentation charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="dce58-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="dce58-121">Types pointeur .NET (p. ex.,</span><span class="sxs-lookup"><span data-stu-id="dce58-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="dce58-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="dce58-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="dce58-123">Type dérivé de `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="dce58-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="dce58-124">Type dérivé de `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="dce58-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="dce58-125">Type `BOOL` Win32</span><span class="sxs-lookup"><span data-stu-id="dce58-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="dce58-126">Struct `DECIMAL` COM</span><span class="sxs-lookup"><span data-stu-id="dce58-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="dce58-127">Délégué .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-127">.NET Delegate</span></span> | <span data-ttu-id="dce58-128">Pointeur de fonction natif</span><span class="sxs-lookup"><span data-stu-id="dce58-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="dce58-129">Type `DATE` Win32</span><span class="sxs-lookup"><span data-stu-id="dce58-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="dce58-130">Type `GUID` Win32</span><span class="sxs-lookup"><span data-stu-id="dce58-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="dce58-131">Certaines catégories ont des valeurs par défaut différentes pour le marshaling comme paramètre ou comme structure.</span><span class="sxs-lookup"><span data-stu-id="dce58-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="dce58-132">Type .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-132">.NET Type</span></span> | <span data-ttu-id="dce58-133">Type natif (paramètre)</span><span class="sxs-lookup"><span data-stu-id="dce58-133">Native Type (Parameter)</span></span> | <span data-ttu-id="dce58-134">Type natif (champ)</span><span class="sxs-lookup"><span data-stu-id="dce58-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="dce58-135">Tableau .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-135">.NET array</span></span> | <span data-ttu-id="dce58-136">Pointeur vers le début d’un tableau de représentations natives des éléments du tableau</span><span class="sxs-lookup"><span data-stu-id="dce58-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="dce58-137">Non autorisé sans attribut `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="dce58-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="dce58-138">Classe avec `LayoutKind` de `Sequential` ou de `Explicit`</span><span class="sxs-lookup"><span data-stu-id="dce58-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="dce58-139">Pointeur vers la représentation native de la classe</span><span class="sxs-lookup"><span data-stu-id="dce58-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="dce58-140">Représentation native de la classe</span><span class="sxs-lookup"><span data-stu-id="dce58-140">The native representation of the class</span></span> |

<span data-ttu-id="dce58-141">Le tableau suivant présente les règles de marshaling par défaut propres à Windows.</span><span class="sxs-lookup"><span data-stu-id="dce58-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="dce58-142">Sur les autres plateformes, il n’est pas possible de marshaler ces types.</span><span class="sxs-lookup"><span data-stu-id="dce58-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="dce58-143">Type .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-143">.NET Type</span></span> | <span data-ttu-id="dce58-144">Type natif (paramètre)</span><span class="sxs-lookup"><span data-stu-id="dce58-144">Native Type (Parameter)</span></span> | <span data-ttu-id="dce58-145">Type natif (champ)</span><span class="sxs-lookup"><span data-stu-id="dce58-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="dce58-146">Interface COM</span><span class="sxs-lookup"><span data-stu-id="dce58-146">COM interface</span></span> | <span data-ttu-id="dce58-147">Non autorisé sans attribut `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="dce58-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="dce58-148">Non autorisé</span><span class="sxs-lookup"><span data-stu-id="dce58-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="dce58-149">Non autorisé</span><span class="sxs-lookup"><span data-stu-id="dce58-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="dce58-150">Non autorisé</span><span class="sxs-lookup"><span data-stu-id="dce58-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="dce58-151"> représentant le nombre de cycles depuis le 1er janvier 1601 à minuit</span><span class="sxs-lookup"><span data-stu-id="dce58-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="dce58-152"> représentant le nombre de cycles depuis le 1er janvier 1601 à minuit</span><span class="sxs-lookup"><span data-stu-id="dce58-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="dce58-153">Certains types ne peuvent être marshalés que comme paramètres, et non comme champs.</span><span class="sxs-lookup"><span data-stu-id="dce58-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="dce58-154">:</span><span class="sxs-lookup"><span data-stu-id="dce58-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="dce58-155">Type .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-155">.NET Type</span></span> | <span data-ttu-id="dce58-156">Type natif (paramètre uniquement)</span><span class="sxs-lookup"><span data-stu-id="dce58-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="dce58-157">`char*` ou `char16_t*` selon le `CharSet` de P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="dce58-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="dce58-158">Voir la [documentation charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="dce58-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="dce58-159">`va_list` (sur Windows x86/x64/arm64 uniquement)</span><span class="sxs-lookup"><span data-stu-id="dce58-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="dce58-160">Si ces valeurs par défaut ne vous conviennent pas tout à fait, vous pouvez personnaliser la façon dont les paramètres sont marshalés.</span><span class="sxs-lookup"><span data-stu-id="dce58-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="dce58-161">L’article [Marshaling des paramètres](customize-parameter-marshaling.md) explique comment faire, pour différents types de paramètres.</span><span class="sxs-lookup"><span data-stu-id="dce58-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="dce58-162">Marshaling par défaut dans les scénarios COM</span><span class="sxs-lookup"><span data-stu-id="dce58-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="dce58-163">Quand vous appelez des méthodes sur des objets COM dans .NET, le runtime .NET modifie les règles de marshaling par défaut pour qu’elles correspondent à la sémantique COM courante.</span><span class="sxs-lookup"><span data-stu-id="dce58-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="dce58-164">Le tableau suivant liste les règles utilisées par les runtimes .NET dans les scénarios COM :</span><span class="sxs-lookup"><span data-stu-id="dce58-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="dce58-165">Type .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-165">.NET Type</span></span> | <span data-ttu-id="dce58-166">Type natif (appels de méthodes COM)</span><span class="sxs-lookup"><span data-stu-id="dce58-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="dce58-167">Types délégués</span><span class="sxs-lookup"><span data-stu-id="dce58-167">Delegate types</span></span> | <span data-ttu-id="dce58-168">`_Delegate*` dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dce58-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="dce58-169">Non autorisé dans .NET Core et .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="dce58-169">Disallowed in .NET Core and .NET 5+.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="dce58-170">Tableau .NET</span><span class="sxs-lookup"><span data-stu-id="dce58-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="dce58-171">`SAFEARRAY` de `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="dce58-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="dce58-172">Marshaling de classes et de structures</span><span class="sxs-lookup"><span data-stu-id="dce58-172">Marshaling classes and structs</span></span>

<span data-ttu-id="dce58-173">Un autre aspect du marshaling de types consiste à passer une structure à une méthode non managée.</span><span class="sxs-lookup"><span data-stu-id="dce58-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="dce58-174">Par exemple, certaines des méthodes non managées nécessitent une structure comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="dce58-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="dce58-175">Il faut dans ce cas créer une classe ou un struct correspondant dans la partie managée de l’environnement pour l’utiliser comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="dce58-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="dce58-176">Toutefois, il ne suffit pas de définir la classe : il est également nécessaire d’indiquer au marshaleur comment mapper des champs de la classe au struct non managé.</span><span class="sxs-lookup"><span data-stu-id="dce58-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="dce58-177">C’est ici qu’intervient l’attribut `StructLayout`.</span><span class="sxs-lookup"><span data-stu-id="dce58-177">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="dce58-178">Le code précédent illustre de manière simple les appels dans la fonction `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="dce58-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="dce58-179">L’élément digne d’intérêt se trouve sur la ligne 4.</span><span class="sxs-lookup"><span data-stu-id="dce58-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="dce58-180">L’attribut spécifie que les champs de la classe doivent être mappés séquentiellement à la structure de l’autre côté (non managé).</span><span class="sxs-lookup"><span data-stu-id="dce58-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="dce58-181">Cela signifie que le nom des champs n’a pas d’importance ; seul leur ordre compte, car il doit correspondre au struct non managé, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dce58-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="dce58-182">Il est possible que le marshaling par défaut de votre structure ne vous convienne pas.</span><span class="sxs-lookup"><span data-stu-id="dce58-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="dce58-183">L’article [Personnaliser le marshaling des structures](./customize-struct-marshaling.md) explique comment personnaliser la façon dont les structures sont marshalées.</span><span class="sxs-lookup"><span data-stu-id="dce58-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
