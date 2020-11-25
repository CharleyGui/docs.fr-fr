---
title: 'Modification avec rupture : ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 provoquée par l’activation de la règle d’analyse du code ca1417.
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760824"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a><span data-ttu-id="3d913-103">AVERTISSEMENT ca1417 : OutAttribute sur le paramètre de chaîne pour P/Invoke</span><span class="sxs-lookup"><span data-stu-id="3d913-103">Warning CA1417: OutAttribute on string parameter for P/Invoke</span></span>

<span data-ttu-id="3d913-104">La [règle de](/visualstudio/code-quality/ca1417) l’analyseur de code .net est activée, par défaut, à partir de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="3d913-104">.NET code analyzer rule [CA1417](/visualstudio/code-quality/ca1417) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="3d913-105">Il génère un avertissement de génération pour toutes les définitions de méthode d’appel de code non [managé (P/Invoke)](../../../../standard/native-interop/pinvoke.md) quand un <xref:System.String> paramètre est passé par valeur et marqué avec <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3d913-105">It produces a build warning for any [Platform Invoke (P/Invoke)](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is passed by value and marked with <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

## <a name="change-description"></a><span data-ttu-id="3d913-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3d913-106">Change description</span></span>

<span data-ttu-id="3d913-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET comprend des [analyseurs de code source .net](../../../../fundamentals/code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d913-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="3d913-108">Plusieurs de ces règles sont activées par défaut, y compris [ca1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="3d913-108">Several of these rules are enabled, by default, including [CA1417](/visualstudio/code-quality/ca1417).</span></span> <span data-ttu-id="3d913-109">Si votre projet contient du code qui enfreint cette règle et est configuré pour traiter les avertissements comme des erreurs, cette modification risque de perturber votre génération.</span><span class="sxs-lookup"><span data-stu-id="3d913-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="3d913-110">La règle ca1417 marque les définitions de méthode [P/Invoke](../../../../standard/native-interop/pinvoke.md) quand un <xref:System.String> paramètre est marqué avec l' <xref:System.Runtime.InteropServices.OutAttribute> attribut et est passé par valeur.</span><span class="sxs-lookup"><span data-stu-id="3d913-110">Rule CA1417 flags [P/Invoke](../../../../standard/native-interop/pinvoke.md) method definitions where a <xref:System.String> parameter is marked with the <xref:System.Runtime.InteropServices.OutAttribute> attribute and is passed by value.</span></span> <span data-ttu-id="3d913-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3d913-111">For example:</span></span>

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

<span data-ttu-id="3d913-112">Le Runtime .NET gère une table, appelée pool interne, qui contient une référence unique à chaque chaîne littérale unique dans un programme.</span><span class="sxs-lookup"><span data-stu-id="3d913-112">The .NET runtime maintains a table, called the intern pool, that contains a single reference to each unique literal string in a program.</span></span> <span data-ttu-id="3d913-113">Si une chaîne internée marquée avec <xref:System.Runtime.InteropServices.OutAttribute> est passée par valeur à une méthode P/Invoke, le runtime peut être déstabilisé.</span><span class="sxs-lookup"><span data-stu-id="3d913-113">If an interned string marked with <xref:System.Runtime.InteropServices.OutAttribute> is passed by value to a P/Invoke method, the runtime can be destabilized.</span></span> <span data-ttu-id="3d913-114">Pour plus d’informations sur l’internement des chaînes, consultez les notes relatives à <xref:System.String.Intern(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3d913-114">For more information about string interning, see the remarks for <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3d913-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3d913-115">Version introduced</span></span>

<span data-ttu-id="3d913-116">5.0</span><span class="sxs-lookup"><span data-stu-id="3d913-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3d913-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3d913-117">Recommended action</span></span>

- <span data-ttu-id="3d913-118">Si vous devez marshaler à nouveau les données de chaîne modifiées vers l’appelant, transmettez la chaîne par référence à la place.</span><span class="sxs-lookup"><span data-stu-id="3d913-118">If you need to marshal modified string data back to the caller, pass the string by reference instead.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- <span data-ttu-id="3d913-119">Si vous n’avez pas besoin de marshaler à nouveau les données de chaîne modifiées vers l’appelant, supprimez simplement <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3d913-119">If you don't need to marshal modified string data back to the caller, simply remove the <xref:System.Runtime.InteropServices.OutAttribute>.</span></span>

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  <span data-ttu-id="3d913-120">Pour plus d’informations, consultez [ca1417](/visualstudio/code-quality/ca1417).</span><span class="sxs-lookup"><span data-stu-id="3d913-120">For more information, see [CA1417](/visualstudio/code-quality/ca1417).</span></span>

- <span data-ttu-id="3d913-121">Pour désactiver complètement l’analyse du code, affectez `EnableNETAnalyzers` à `false` la valeur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="3d913-121">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="3d913-122">Pour plus d’informations, consultez [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="3d913-122">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3d913-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="3d913-123">Affected APIs</span></span>

<span data-ttu-id="3d913-124">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="3d913-124">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
