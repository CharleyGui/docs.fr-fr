---
title: La mondialisation config paramètres
description: Découvrez les paramètres de run-time qui configurent les aspects de la mondialisation d’une application .NET Core, par exemple, comment elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733454"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="0e931-103">Options de configuration en temps de course pour la mondialisation</span><span class="sxs-lookup"><span data-stu-id="0e931-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="0e931-104">Mode invariant</span><span class="sxs-lookup"><span data-stu-id="0e931-104">Invariant mode</span></span>

- <span data-ttu-id="0e931-105">Détermine si une application .NET Core fonctionne en mode invariant mondialisation sans accès à des données et à un comportement spécifiques à la culture ou si elle a accès à des données culturelles.</span><span class="sxs-lookup"><span data-stu-id="0e931-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="0e931-106">Défaut : Exécutez l’application`false`avec accès aux données culturelles ( ).</span><span class="sxs-lookup"><span data-stu-id="0e931-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="0e931-107">Pour plus d’informations, voir [.NET Core globalisation en mode invariant](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="0e931-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="0e931-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="0e931-108">Setting name</span></span> | <span data-ttu-id="0e931-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="0e931-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0e931-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0e931-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="0e931-111">`false`- accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="0e931-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="0e931-112">`true`- exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="0e931-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0e931-113">**Propriété MSBuild**</span><span class="sxs-lookup"><span data-stu-id="0e931-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="0e931-114">`false`- accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="0e931-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="0e931-115">`true`- exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="0e931-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0e931-116">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="0e931-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="0e931-117">`0`- accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="0e931-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="0e931-118">`1`- exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="0e931-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="0e931-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="0e931-119">Examples</span></span>

<span data-ttu-id="0e931-120">*fichier runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="0e931-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="0e931-121">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="0e931-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="0e931-122">Gammes d’années d’époque</span><span class="sxs-lookup"><span data-stu-id="0e931-122">Era year ranges</span></span>

- <span data-ttu-id="0e931-123">Détermine si les contrôles de portée pour les calendriers qui prennent en charge plusieurs <xref:System.ArgumentOutOfRangeException>époques sont assouplis ou si les dates qui débordent de la plage de date d’une époque jeter un .</span><span class="sxs-lookup"><span data-stu-id="0e931-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="0e931-124">Défaut : Les contrôles`false`de portée sont détendus ( ).</span><span class="sxs-lookup"><span data-stu-id="0e931-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="0e931-125">Pour plus d’informations, voir [Calendriers, époques et plages de dates: Vérifications de portée détendue](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="0e931-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="0e931-126">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="0e931-126">Setting name</span></span> | <span data-ttu-id="0e931-127">Valeurs</span><span class="sxs-lookup"><span data-stu-id="0e931-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0e931-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0e931-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="0e931-129">`false`- contrôles de portée détendus</span><span class="sxs-lookup"><span data-stu-id="0e931-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="0e931-130">`true`- les débordements causent une exception</span><span class="sxs-lookup"><span data-stu-id="0e931-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="0e931-131">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="0e931-131">**Environment variable**</span></span> | <span data-ttu-id="0e931-132">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-132">N/A</span></span> | <span data-ttu-id="0e931-133">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="0e931-134">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="0e931-134">Japanese date parsing</span></span>

- <span data-ttu-id="0e931-135">Détermine si une chaîne qui contient soit "1" ou "Gannen" que l’année analyse avec succès ou si seulement "1" est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0e931-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="0e931-136">Défaut: Parse cordes qui contiennent soit "1" ou "Gannen" comme l’année (`false`).</span><span class="sxs-lookup"><span data-stu-id="0e931-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="0e931-137">Pour plus d’informations, voir [Les dates de représentation dans les calendriers à plusieurs époques](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0e931-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0e931-138">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="0e931-138">Setting name</span></span> | <span data-ttu-id="0e931-139">Valeurs</span><span class="sxs-lookup"><span data-stu-id="0e931-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0e931-140">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0e931-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="0e931-141">`false`- "Gannen" ou "1" est soutenu</span><span class="sxs-lookup"><span data-stu-id="0e931-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="0e931-142">`true`- seul "1" est pris en charge</span><span class="sxs-lookup"><span data-stu-id="0e931-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="0e931-143">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="0e931-143">**Environment variable**</span></span> | <span data-ttu-id="0e931-144">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-144">N/A</span></span> | <span data-ttu-id="0e931-145">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="0e931-146">Format de l’année japonaise</span><span class="sxs-lookup"><span data-stu-id="0e931-146">Japanese year format</span></span>

- <span data-ttu-id="0e931-147">Détermine si la première année d’une ère de calendrier japonaise est formatée comme "Gannen" ou en nombre.</span><span class="sxs-lookup"><span data-stu-id="0e931-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="0e931-148">Défaut: Format de la première année`false`comme "Gannen" ( ).</span><span class="sxs-lookup"><span data-stu-id="0e931-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="0e931-149">Pour plus d’informations, voir [Les dates de représentation dans les calendriers à plusieurs époques](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0e931-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0e931-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="0e931-150">Setting name</span></span> | <span data-ttu-id="0e931-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="0e931-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0e931-152">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0e931-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="0e931-153">`false`- format comme "Gannen"</span><span class="sxs-lookup"><span data-stu-id="0e931-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="0e931-154">`true`- format comme numéro</span><span class="sxs-lookup"><span data-stu-id="0e931-154">`true` - format as number</span></span> |
| <span data-ttu-id="0e931-155">**Variable de l’environnement**</span><span class="sxs-lookup"><span data-stu-id="0e931-155">**Environment variable**</span></span> | <span data-ttu-id="0e931-156">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-156">N/A</span></span> | <span data-ttu-id="0e931-157">N/A</span><span class="sxs-lookup"><span data-stu-id="0e931-157">N/A</span></span> |
