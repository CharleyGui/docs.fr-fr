---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 7668c345181d7c08cfca9c5cb76b8addd76223ec
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506803"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="4e426-103">Options de configuration au moment de l’exécution pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="4e426-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="4e426-104">Mode indifférent</span><span class="sxs-lookup"><span data-stu-id="4e426-104">Invariant mode</span></span>

- <span data-ttu-id="4e426-105">Détermine si une application .NET Core s’exécute en mode globalisation-invariant sans accéder aux données et au comportement spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="4e426-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="4e426-106">Par défaut : exécutez l’application avec un accès aux données`false`culturelles ().</span><span class="sxs-lookup"><span data-stu-id="4e426-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="4e426-107">Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="4e426-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="4e426-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4e426-108">Setting name</span></span> | <span data-ttu-id="4e426-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4e426-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4e426-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4e426-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="4e426-111">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="4e426-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="4e426-112">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="4e426-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="4e426-113">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="4e426-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="4e426-114">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="4e426-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="4e426-115">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="4e426-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="4e426-116">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4e426-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="4e426-117">`0`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="4e426-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="4e426-118">`1`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="4e426-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="4e426-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="4e426-119">Examples</span></span>

<span data-ttu-id="4e426-120">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="4e426-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="4e426-121">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="4e426-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="4e426-122">Plages d’années d’ère</span><span class="sxs-lookup"><span data-stu-id="4e426-122">Era year ranges</span></span>

- <span data-ttu-id="4e426-123">Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui <xref:System.ArgumentOutOfRangeException>dépassent la plage de dates d’une ère lèvent un.</span><span class="sxs-lookup"><span data-stu-id="4e426-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="4e426-124">Valeur par défaut : les contrôles de`false`plage sont assouplis ().</span><span class="sxs-lookup"><span data-stu-id="4e426-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="4e426-125">Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="4e426-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="4e426-126">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4e426-126">Setting name</span></span> | <span data-ttu-id="4e426-127">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4e426-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4e426-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4e426-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="4e426-129">`false`-vérifications de plage souples</span><span class="sxs-lookup"><span data-stu-id="4e426-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="4e426-130">`true`-les dépassements de capacité provoquent une exception</span><span class="sxs-lookup"><span data-stu-id="4e426-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="4e426-131">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4e426-131">**Environment variable**</span></span> | <span data-ttu-id="4e426-132">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-132">N/A</span></span> | <span data-ttu-id="4e426-133">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="4e426-134">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="4e426-134">Japanese date parsing</span></span>

- <span data-ttu-id="4e426-135">Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4e426-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="4e426-136">Valeur par défaut : analyser les chaînes qui contiennent soit « 1 » soit « gannen » comme`false`année ().</span><span class="sxs-lookup"><span data-stu-id="4e426-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="4e426-137">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="4e426-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="4e426-138">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4e426-138">Setting name</span></span> | <span data-ttu-id="4e426-139">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4e426-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4e426-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4e426-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="4e426-141">`false`-« Gannen » ou « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="4e426-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="4e426-142">`true`seule « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="4e426-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="4e426-143">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4e426-143">**Environment variable**</span></span> | <span data-ttu-id="4e426-144">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-144">N/A</span></span> | <span data-ttu-id="4e426-145">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="4e426-146">Format d’année japonaise</span><span class="sxs-lookup"><span data-stu-id="4e426-146">Japanese year format</span></span>

- <span data-ttu-id="4e426-147">Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.</span><span class="sxs-lookup"><span data-stu-id="4e426-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="4e426-148">Valeur par défaut : mettez en forme la première année sous`false`la forme « gannen » ().</span><span class="sxs-lookup"><span data-stu-id="4e426-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="4e426-149">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="4e426-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="4e426-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="4e426-150">Setting name</span></span> | <span data-ttu-id="4e426-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="4e426-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4e426-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="4e426-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="4e426-153">`false`-format comme « gannen »</span><span class="sxs-lookup"><span data-stu-id="4e426-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="4e426-154">`true`-format comme nombre</span><span class="sxs-lookup"><span data-stu-id="4e426-154">`true` - format as number</span></span> |
| <span data-ttu-id="4e426-155">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="4e426-155">**Environment variable**</span></span> | <span data-ttu-id="4e426-156">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-156">N/A</span></span> | <span data-ttu-id="4e426-157">N/A</span><span class="sxs-lookup"><span data-stu-id="4e426-157">N/A</span></span> |
